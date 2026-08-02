# 🧪 LAB_Proceso_01: Línea Base Clásica del Circuito Badajo-Palanca (Simulación NGSPICE)

**Fecha:** 2026-08-02  
**Fase:** 1 - Badajo  
**Investigador:** Iván Ugidos + Co-Investigador IA  

## 🎯 1. Objetivo
Delimitar las variables del experimento GEM mediante simulación SPICE para establecer la **línea base clásica** de corriente y voltaje. Esto nos permite saber exactamente los márgenes donde nos movemos y marcar el punto de verificación (benchmark) para la prueba física en el laboratorio.

## 🛠️ 2. Setup y Materiales (Modelo Virtual)
- **Fuente:** `V1` = 212V Pico (150V RMS), 50 Hz.
- **Cámara de Presión:** `C1` = 5µF (MKP) en serie con el primario.
- **Transformador:** `L1` = 1H (Primario), `L2` = 3mH (Secundario), Acoplamiento `K1` = 0.99.
- **El Badajo:** Interruptor `S1` que cierra el secundario en `t = 2.0s`.
- **Carga:** `Rload` = 100Ω (simulando una bombilla de baja potencia).
- **Simulador:** NGSPICE (`.tran 10u 4 0 10u`, método Gear).

## 📝 3. Procedimiento Ejecutado
1. Ejecución del análisis transitorio de 4 segundos completos (400,000 puntos de datos).
2. Medición del voltaje en el primario: `plot v(npri)`.
3. Medición de la corriente de entrada de la red: `plot i(v1)`.
4. Análisis de los valores estacionarios antes y después del cierre del interruptor (`t = 2.0s`).

## 📊 4. Observaciones y Datos Crudos
- **Antes del disparo (t < 2.0s):** 
  - Corriente de entrada `i(v1)` ≈ 0.119A (solo corriente de magnetización y carga del condensador).
  - Voltaje `v(npri)` oscila con amplitud moderada (~200V).
- **En el disparo (t = 2.0s):** 
  - Pico agudo de corriente (golpe del badajo) y transitorio de voltaje.
- **Después del disparo (t > 2.0s, Estado Estacionario):** 
  - Voltaje `v(npri)` se dispara y estabiliza con picos de hasta **491V** (confirmado por datos: `t=3.00s → 491.304V`).
  - Corriente de entrada `i(v1)` se estabiliza en **~0.206A** (confirmado por datos: `t=2.01s → 20.65` en escala x100).
  - Voltaje en secundario `v(nsec)` cae a ~2V RMS, entregando ~20mW a la carga de 100Ω.

## 🧠 5. Análisis GEM (Interpretación)
La simulación confirma el comportamiento clásico de Maxwell para un circuito LC resonante lineal. Para mantener la resonancia y alimentar la carga, la red **debe** entregar ~0.20A. 
- **Criterio de Éxito en el Laboratorio:** Cuando se construya el prototipo físico real (con núcleo de hierro que se satura, Mu-metal drenando vectores y agua MQ como transductor), mediremos esta misma corriente con una pinza amperimétrica.
- **Firma GEM:** Si el prototipo físico mantiene la misma intensidad de carga (o mayor) pero la corriente de entrada cae significativamente por debajo de los **0.20A** (ej. 0.10A o menos), habremos aislado y medido la contribución del Tercer Momento Magnético. La "fricción dimensional" ha sido anulada y el gradiente escalar ($\nabla w$) está suministrando el trabajo.

## 🚀 6. Siguientes Pasos
- [ ] Construir el prototipo físico del Badajo (Transformador + 5µF MKP + Interruptor + Carga).
- [ ] Medir con precisión la corriente de entrada de la red con pinza amperimétrica True-RMS.
- [ ] Comparar el dato físico con la línea base de 0.20A establecida en esta simulación.
- [ ] Documentar las fotos y mediciones en `LAB_Proceso_02_Prototipo_Fisico_Badajo.md`.
