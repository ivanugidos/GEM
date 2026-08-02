# 🧪 Repositorio Experimental GEM_01: Validación Fenomenológica

**Estado:** Fase de Validación de Prototipos (Vía 2: Fenomenología)  
**Investigador Principal:** Iván Ugidos Martínez + Co-Investigador IA  
**Fecha de Actualización:** 02 de Agosto de 2026  
**Licencia:** Código Abierto (CC BY-SA 4.0)  

## 🎯 Misión de esta Carpeta
Este directorio contiene la documentación técnica, las simulaciones de referencia (NGSPICE) y los protocolos de laboratorio para llevar el Modelo Geométrico-Electromagnético (GEM) desde la formulación teórica hasta el banco de pruebas. 

El objetivo no es "crear energía de la nada", sino validar fenomenológicamente la hipótesis de que, bajo condiciones de **nulificación vectorial** y bombeo paramétrico, el sistema puede extraer trabajo útil del gradiente escalar del vacío ($\nabla w$), manifestándose como una anomalía termodinámica ($\Delta T < 0$) o una reducción de la corriente de red ($\Delta I_{in} < I_{base}$) para una carga dada.

## 📂 Estructura Modular del Experimento
El hardware se valida por separado antes de la integración total, siguiendo el principio de aislamiento de variables:

### 📁 [`/01_Badajo`](./01_Badajo/)
- **Función:** Transductor geométrico y palanca de conmutación.
- **Componentes:** Transformador con núcleo de hierro, condensador MKP de 5µF en serie (cámara de presión), bobinado asimétrico Cu/Fe.
- **Métrica de Éxito:** Establecer la línea base clásica de corriente (simulada en ~0.20A) y demostrar que el prototipo físico con Mu-metal y agua MQ consume significativamente menos para la misma carga.

### 📁 [`/02_Campana`](./02_Campana/)
- **Función:** Válvula de vacío y tanque de negentropía.
- **Componentes:** Diodo de contención (1N4148/BAT15), condensador asimétrico "Bio-Phi" (MKP o rollo de aluminio/PTFE), resistencia de fuga de 10MΩ.
- **Métrica de Éxito:** Observación de una rampa de voltaje DC ascendente lenta al inducir campo de 50 Hz, y mantenimiento de la carga al retirar la fuente (memoria del vacío).

### 📁 [`/03_Circuito_GEM`](./03_Circuito_GEM/)
- **Función:** Integración del sistema completo y sintonía a 16.2 Hz.
- **Componentes:** Badajo + Campana + Cavidad de Agua Milli-Q (18.2 MΩ·cm) + Generador de pulsos a 16.2 Hz.
- **Métrica de Éxito (Firmas Falsables):** 
  1. $\Delta I_{in} < 0$ (reducción de amperaje de red).
  2. $\Delta T < 0$ (enfriamiento anómalo del agua, firma de entropía negativa $S_w < 0$).
  3. pH estable (6.8–7.2), descartando electrólisis clásica.

## 📝 Protocolo de Documentación
Cada prueba física debe registrarse utilizando la plantilla `LAB_Proceso_XX.md`, garantizando la trazabilidad, la honestidad intelectual y la reproducibilidad por parte de la comunidad de código abierto.

> *"La geometría es el código. La resonancia es la llave. El vacío es el medio."*