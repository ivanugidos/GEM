* ========================================================================
* PRUEBA DE VALIDACIÓN: ETAPA 3 (LA COSECHA) AISLADA
* ========================================================================

* Simulamos que la antena bifilar ya captó una señal escalar de 1.5V de pico
V_ant N_Antena 0 SIN(0 1.5 14.28Meg)

* Etapa 3: Rectificador y Filtro
D1 N_Antena N_Rect BAT15
C1 N_Rect 0 100p
C2 N_Rect 0 1n
R_load N_Rect 0 1Meg

* Modelo del Diodo
.model BAT15 D (IS=2.0E-8 N=1.04 RS=2.5 CJO=0.5E-12 VJ=0.65 M=0.6 EG=1.16 XTI=2.0 FC=0.5 BV=4.0 IBV=500E-9)

* Simulación rápida (solo unos pocos microsegundos para ver la carga)
.tran 0 10u 0 1n

.control
  run
  plot v(N_Antena) v(N_Rect) title "Validación Etapa 3: Carga del Condensador"
.endc

.end