* ========================================================================
* GEM-LITE: Simulación del Kit de Validación de Mesa
* Bobinado bifilar en clavo de hierro + Duplicador de Tensión (Villard)
* Frecuencia: 16.2 Hz (Onda Cuadrada Abrupta)
* ========================================================================

* --- FUENTE DE SEÑAL (Smartphone / Generador) ---
* Onda cuadrada de 16.2 Hz, 3V de amplitud.
* Flancos de subida/bajada de 1us (Pulsos abruptos para esquivar histéresis).
* Periodo = 61.7ms, Ancho de pulso = 30.85ms (Ciclo de trabajo 50%)
V_in In 0 PULSE(0 3 0 1u 1u 30.85m 61.7m)

* --- BOBINADO BIFILAR EN NÚCLEO DE HIERRO ---
* Modelo simplificado: Dos inductores acoplados magnéticamente.
* AWG 26 (Emisor) y AWG 29 (Colector) enrollados juntos.
* L = 50mH cada uno (aprox. para clavo de hierro 10cm, 250 espiras).
* Resistencia serie: 1.5 Ohm (AWG26) y 3.0 Ohm (AWG29).
L_emisor In N_mid 50mH Rser=1.5
L_colector N_mid 0 50mH Rser=3.0

* Acoplamiento magnético fuerte (k=0.95) en el mismo núcleo de hierro
K1 L_emisor L_colector 0.95

* --- CIRCUITO DE COSECHA: DUPLICADOR DE TENSIÓN DE MEDIA ONDA ---
* Esta es la "Bomba de Carga" que acumula los pulsos escalares.

* C1: Condensador de bombeo (se carga en el semiciclo negativo)
C1 In N_bomba 100n

* D1: Diodo de carga de C1
* Ánodo en GND, Cátodo en N_bomba
D1 0 N_bomba SCHOTTKY

* D2: Diodo de transferencia a C2 (se activa en el semiciclo positivo)
* Ánodo en N_bomba, Cátodo en Out
D2 N_bomba Out SCHOTTKY

* C2: Condensador de almacenamiento / filtro (Aquí se acumula la energía)
C2 Out 0 1u

* R_load: Carga de trabajo (10k para medir en alta impedancia)
R_load Out 0 10k

* --- MODELO DEL DIODO SCHOTTKY (1N5817 / BAT15) ---
* Diodo rápido con baja caída de tensión (~0.3V)
.model SCHOTTKY D (IS=2.0E-8 N=1.04 RS=0.5 CJO=0.5E-12 VJ=0.65 M=0.6 EG=1.16 XTI=2.0 FC=0.5 BV=40 IBV=500E-9)

* --- SIMULACIÓN TRANSITORIA ---
* Simulamos 1 segundo completo (aprox 16 ciclos de 16.2 Hz)
.tran 10u 1 0 10u
.options abstol=1e-12 reltol=1e-6 vntol=1e-9

* --- MEDICIONES ---
.meas tran V_out_final AVG V(Out) FROM=0.8 TO=1.0
.meas tran I_in_avg AVG I(V_in) FROM=0.8 TO=1.0

* --- BLOQUE DE CONTROL PARA VISUALIZACIÓN ---
.control
  run
  echo "=== RESULTADOS GEM-LITE (Kit de Mesa) ==="
  print V_out_final
  print I_in_avg
  echo "==========================================="
  
  * Gráfica 1: Voltaje de entrada (Pulsos) vs Voltaje de salida DC
  plot v(In) v(Out) title "GEM-Lite: Entrada 16.2Hz vs Salida DC (Bomba de Carga)"
  
  * Gráfica 2: Detalle de cómo C2 se va cargando ciclo a ciclo
  plot v(Out) title "Carga del Condensador C2 en el tiempo (1 seg)"
.endc

.end