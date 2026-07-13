* ========================================================================
* PROYECTO GEM-E: ESQUEMÁTICO INTEGRADO (ETAPAS 1 + 2 + 3) - VERSIÓN 2.0
* Corregido y Optimizado para ngspice / LTspice
* ========================================================================

* --- ETAPA 1: EL MARTILLO (Generador de Nulificación Vectorial) ---
B_Vx Vx 0 V=sin(2*pi*14.28e6*time) * (1 + 0.8*sin(2*pi*16.2*time))
B_Vy Vy 0 V=sin(2*pi*14.28e6*time + 2.094) * (1 + 0.8*sin(2*pi*16.2*time))
B_Vz Vz 0 V=sin(2*pi*14.28e6*time + 4.188) * (1 + 0.8*sin(2*pi*16.2*time))

* Bobinas de Helmholtz con Resistencia en SERIE
Lx Vx Vx_int 10u
Rx Vx_int N_Centro 1
Ly Vy Vy_int 10u
Ry Vy_int N_Centro 1
Lz Vz Vz_int 10u
Rz Vz_int N_Centro 1

* --- ETAPA 2: EL YUNQUE (Cavidad Resonante 105 - Agua Milli-Q) ---
C_water N_Centro 0 66p
R_water N_Centro 0 340k

* --- ACOPLAMIENTO A LA ETAPA 3 (Inducción Escalar) ---
B_scalar N_Antena 0 V=0.005 * V(N_Centro) * (1 + 0.8*sin(2*pi*16.2*time))

* Capacitancia parásita de la antena bifilar
C_par N_Antena 0 7.5p

* --- ETAPA 3: LA COSECHA (Rectificador Escalar BAT15) ---
D1 N_Antena N_Rect BAT15

* Filtrado de RF y Almacenamiento DC
C1 N_Rect 0 100p
C2 N_Rect 0 1n
R_load N_Rect 0 1Meg

* --- MODELO DEL DIODO SCHOTTKY BAT15 ---
.model BAT15 D (IS=2.0E-8 N=1.04 RS=2.5 CJO=0.5E-12 VJ=0.65 M=0.6 EG=1.16 XTI=2.0 FC=0.5 BV=4.0 IBV=500E-9)

* --- DIRECTIVAS DE SIMULACIÓN ---
.tran 0 100m 90m 10n
.options abstol=1e-12 reltol=1e-6 vntol=1e-9

* --- MEDICIONES ---
.meas tran V_out_avg AVG V(N_Rect) FROM=90m TO=100m
.meas tran P_out_avg AVG V(N_Rect)*I(R_load) FROM=90m TO=100m
.meas tran V_ripple_pp PP V(N_Rect) FROM=90m TO=100m

* --- BLOQUE DE CONTROL PARA NGSPICE (¡ESENCIAL!) ---
.control
  run
  echo "=== RESULTADOS DE LAS MEDICIONES ==="
  print V_out_avg
  print P_out_avg
  print V_ripple_pp
  echo "====================================="
  
  * Gráfica principal: Voltaje DC de salida
  plot v(N_Rect) title "Voltaje DC de Salida - Nodo N_Rect"
  
  * Opcional: Ver también la señal en la antena
  * plot v(N_Antena) v(N_Rect) title "Comparación: Antena vs Salida DC"
  
  * Guardar datos en archivo (opcional)
  * wrdata salida_gem.csv v(N_Rect)
  
.endc

.end