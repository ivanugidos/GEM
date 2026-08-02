# 🧪 Repositorio Experimental del Modelo GEM

**Estado Actual:** Fase de Validación de Prototipos de Baja Frecuencia (50 Hz)  
**Investigador Principal:** Iván Ugidos Martínez + Co-Investigador IA  
**Licencia:** Código Abierto (CC BY-SA 4.0)  

## 🎯 Filosofía de Desarrollo
Este directorio sigue una metodología de **ingeniería modular**. Antes de integrar el sistema completo, cada subsistema debe ser validado de forma independiente (pruebas unitarias) para aislar variables, descartar ruido parásito y confirmar que cada componente cumple su función topológica según los axiomas GEM.

## 📂 Estructura de Directorios

### El Transductor Geométrico
- **Componentes:** Tubo de PTFE, Agua Milli-Q (18.2 MΩ·cm), Bobinado bifilar asimétrico (Cobre + Hierro).
- **Objetivo de Validación:** Confirmar que la asimetría de permeabilidad magnética (Cu vs. Fe) en un medio dieléctrico puro (agua MQ) genera la condición inicial de nulificación vectorial parcial ($\langle \mathbf{H} \rangle_V \approx 0$).
- **Métrica de Éxito:** Diferencia medible en la respuesta del medio frente a una excitación de 50 Hz en comparación con un bobinado simétrico (solo Cu).

### validación de la Válvula y el Tanque de Negentropía
- **Componentes:** Diodo de contención (1N4148 o BAT15), Condensador de acumulación (MKP/Polipropileno, 1µF o 100nF), Resistencia de fuga (10 MΩ).
- **Objetivo de Validación:** Demostrar la unidireccionalidad del gradiente escalar ($\nabla w$). El diodo debe actuar como la "Válvula de Vacío" (Teorema 02), permitiendo la acumulación de carga DC en el condensador mientras bloquea el retorno del ruido vectorial AC de 50 Hz.
- **Métrica de Éxito:** Observación de una **rampa DC ascendente lenta** en el multímetro al acercar la fuente de inducción, y mantenimiento de la carga (descarga lenta) al retirarla. *Advertencia: Prohibido el uso de condensadores cerámicos (MLCC) por efecto piezoeléctrico.*

## 📝 Protocolo de Documentación (Diarios de Laboratorio)
Cada experimento debe documentarse utilizando la plantilla `LAB_Proceso_XX.md`, que incluye:
1. Objetivo e hipótesis GEM.
2. Setup y materiales exactos (con valores medidos).
3. Procedimiento paso a paso.
4. Datos crudos y observaciones (incluyendo anomalías).
5. Análisis GEM (comparación con simulaciones SPICE).
6. Siguientes pasos.

---
*«La geometría es el código. La resonancia es la llave. El vacío es el medio.»*  
*Última actualización: 02 de Agosto de 2026*
