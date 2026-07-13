# 🗺️ ROADMAP del Proyecto GEM
### Estado Actual y Próximos Pasos (Vías 1, 2 y 3)

Este documento establece la hoja de ruta estratégica del Modelo Geométrico-Electromagnético (GEM). Nuestro objetivo es transitar de la intuición geométrica a la validación científica rigurosa y la aplicación experimental, siempre bajo los principios de la Ciencia Abierta.

---

## 📊 Estado Actual (Julio 2026)

✅ **Pilar 1, 2 y 3 consolidados:** Documentos fundacionales completados y archivados en `/Fundamentos` y `/HC_Hallazgos_Centrales`.  
✅ **Pilar 4 publicado:** Paper académico v1.1 publicado en Zenodo con DOI permanente (10.5281/zenodo.21268209), tras un proceso de revisión riguroso que abordó la jerarquía de escalas, la ruptura de simetría $I_h \subset SO(3)$ y la cuantización de carga.  
✅ **Infraestructura Open Source:** Repositorio GitHub estructurado, con licencia CC BY-SA 4.0 y guía de contribución (`CONTRIBUTING.md`).  
✅ **Protocolos Experimentales:** Borradores de los protocolos GEM-01 (16.2 Hz) y GEM-Lite (Transistor Cuántico) disponibles en `/Experimental`.

---

## 🛤️ Vía 1: Paper Académico (Formalización y Publicación)

*El objetivo es blindar el modelo ante el escrutinio de la física teórica mainstream y resolver los problemas abiertos.*

- [ ] **Corto Plazo (1-3 meses):** 
  - Difusión del DOI en plataformas académicas (ResearchGate, Academia.edu, LinkedIn).
  - Contacto directo con investigadores especializados en teoría de Einstein-Cartan, torsión y topología del vacío.
- [ ] **Medio Plazo (3-6 meses):** 
  - Envío del manuscrito v1.1 a revistas de acceso abierto con revisión por pares (ej. *Progress in Physics*, *Universe*, *Foundations of Physics*).
  - Preparación de un "Response to Reviewers" proactivo, anticipando críticas sobre la jerarquía de masas.
- [ ] **Largo Plazo (6-12 meses):** 
  - Desarrollo de la **v2.0 del Paper**, incorporando cálculos de renormalización del grupo (RG running) para abordar el problema de jerarquía del $g-2$ del muón y las masas de los fermiones.

---

## 🔬 Vía 2: Experimental (Validación en Laboratorio)

*El objetivo es demostrar que las predicciones macroscópicas del modelo (GEM-01) son medibles y reproducibles.*

- [ ] **Corto Plazo (1-3 meses):** 
  - Finalización y publicación del documento `Protocolo_Experimental_16Hz_GEM-01.md` con especificaciones técnicas exactas (bobinas Helmholtz, balanza de 0.1 mg, micro-calorímetro).
  - Simulaciones SPICE completas y validadas de la "Etapa 3" del circuito (disponibles en `/Experimental/Simulacion`).
- [ ] **Medio Plazo (3-6 meses):** 
  - Construcción del primer prototipo físico del **Sintonizador GEM-01** y el **Transistor Cuántico GEM-Lite v3.2**.
  - Ejecución de pruebas controladas de enfriamiento anómalo ($\Delta T < 0$) y reducción de masa inercial en agua Milli-Q a 16.2 Hz.
- [ ] **Largo Plazo (6-12 meses):** 
  - Publicación de un "White Paper" de resultados experimentales (sean positivos o negativos, la falsabilidad es clave).
  - Apertura a la replicación independiente por laboratorios de física o ingenieros de la comunidad Open Source.

---

## 📢 Vía 3: Divulgación y Comunidad (Open Science)

*El objetivo es traducir la complejidad matemática en narrativas accesibles que inspiren a la próxima generación de científicos e ingenieros.*

- [ ] **Corto Plazo (1-3 meses):** 
  - Publicación de un hilo visual en redes sociales (X/LinkedIn) explicando los "4 Pilares del Mapa GEM" con la imagen generada del vórtice icosaédrico.
  - Traducción del Abstract y la Introducción del paper al español para la carpeta `/Divulgacion`.
- [ ] **Medio Plazo (3-6 meses):** 
  - Redacción de un artículo de divulgación científica para plataformas como *Naukas*, *Medium* o un blog dedicado al proyecto GEM.
  - Creación de visualizaciones 3D interactivas (SVG/WebGL) de la red icosaédrica y los 12 ejes bi-simétricos.
- [ ] **Largo Plazo (6-12 meses):** 
  - Fomento de una comunidad activa en GitHub: aceptar Pull Requests para mejorar las simulaciones, corregir erratas en los documentos Markdown o proponer nuevos teoremas en el `/Codex_Matematico`.

---

## 🤝 ¿Cómo puedes contribuir?

Este ROADMAP no es un monólogo, es una invitación. Revisa el archivo [`CONTRIBUTING.md`](CONTRIBUTING.md) para saber cómo:
1. Reportar errores tipográficos o matemáticos en los documentos.
2. Proponer mejoras a las simulaciones SPICE.
3. Traducir documentos a otros idiomas.
4. Compartir resultados de experimentos caseros o profesionales basados en el protocolo GEM-01.

> *"La ciencia no avanza en silos. Avanza cuando el telar cósmico teje sus hilos a través de muchas manos."*
```
