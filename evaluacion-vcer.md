# Evaluación VCER: catálogo de aplicaciones de matemática (`repoapps_mate`)

Rúbrica VCER: Recomendable (90 %)  
Versión evaluada: Repositorio curado `repoapps_mate` (7 aplicaciones didácticas de matemática en HTML/CSS/JS para secundaria y nivel superior, nota de decisiones `DECISIONES.md`, licencia dual libre y apoyos DUA integrados), 27 de octubre de 2026.

Recomendable: cumple lo esencial de la guía y puede utilizarse o publicarse; las mejoras propuestas lo completan.

---

## 1. Inventario completo del recurso

- **Tratamiento y almacenamiento de datos personales:**
  - El catálogo y la totalidad de sus aplicaciones funcionan de forma local en el navegador del usuario.
  - Ninguna herramienta solicita nombres, apellidos, correos electrónicos ni información identificatoria del alumnado.
  - **Persistencia:** Solo la aplicación `cintia.html` utiliza almacenamiento local (`localStorage`) para registrar el avance numérico en las misiones (`cMis`) y las estrellas obtenidas (`cEst`), guardando exclusivamente datos de juego anónimos en el dispositivo del estudiante.
  - **Analítica de terceros:** Cero rastreadores. No contiene Google Analytics, Google Tag Manager, Microsoft Clarity, Meta Pixel ni telemetría externa.
  - **Comunicaciones salientes:** Cero llamadas de red salientes (`fetch`, `XMLHttpRequest`, `axios`).

- **Direcciones externas y dependencias de código:**
  - `https://fonts.googleapis.com` y `https://fonts.gstatic.com`: Servicio de tipografías web de Google Fonts (*Outfit*, *Space Grotesk*, *Inter*, *Press Start 2P*, *VT323*).
  - `https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/` y `6.0.0`: Iconografía vectorial accesible de FontAwesome.
  - `https://cdn.tailwindcss.com`: Framework de utilidades CSS en tiempo de ejecución (utilizado en `alicia.html` y `escape_geometrico.html`).
  - *Comportamiento sin internet:* Si el repositorio se abre descargado en una computadora sin conexión a internet, las tipografías son sustituidas automáticamente por las fuentes genéricas del sistema operativo (*sans-serif*, *monospace*) y los iconos vectoriales de FontAwesome se mostrarán como recuadros vacíos. En las dos aplicaciones vinculadas a Tailwind CDN (`alicia.html` y `escape_geometrico.html`), se mantendrán la lógica, controles y contenidos, adaptándose a los estilos base del navegador.

- **Imágenes, audio y recursos multimedia:**
  - Cero dependencias de servidores de imágenes externos para las aplicaciones didácticas.
  - Todas las representaciones gráficas (parábolas, esquemas de Ruffini, fracciones, cuerpos geométricos y figuras de pixel art) están construidas de forma nativa mediante gráficos vectoriales SVG incrustados en el código o dibujadas mediante lienzo Canvas HTML5.
  - No se emplean archivos de audio externos; la accesibilidad auditiva se apoya en la síntesis de voz nativa del navegador (Web Speech API).

---

## 2. Puntuación y justificación de los diez criterios VCER

### 1. Contenido (eliminatorio) — Puntuación: 2 / 2
No se detectan errores en lo que enseña: los algoritmos algebraicos de división sintética (`app_ruffini_dua.html` y `ruffini.htm`), la evaluación lógica de tablas de verdad con clasificación formal en tautología, contradicción o contingencia (`actividad_tablas_verdad.html`), las relaciones métricas y transformaciones geométricas en SVG (`arte_matematica.html` y `escape_geometrico.html`), el cálculo de volumen y superficie de envases cilíndricos y prismáticos (`alicia.html`) y las equivalencias fraccionarias con reparto equitativo (`cintia.html`) son conceptual y matemáticamente rigurosos.

### 2. Datos personales (eliminatorio) — Puntuación: 2 / 2
No pide datos que identifiquen a nadie, no incorpora analítica ni herramientas de rastreo y no envía información a servidores externos; la única persistencia se realiza localmente en el dispositivo para registrar el progreso lúdico de misiones y estrellas en el simulador de fracciones sin solicitar nombres ni cuentas de usuario.

### 3. Entender qué hace — Puntuación: 2 / 2
El repositorio es un catálogo interactivo que clasifica y ejecuta herramientas didácticas de matemática para educación secundaria y superior mediante filtrado temático en tiempo real; ninguna herramienta guarda datos personales ni se comunica con servicios externos, funcionando de manera autónoma en el navegador y coincidiendo plenamente lo que declara el catálogo con lo que ejecuta el código.

### 4. Dependencias — Puntuación: 2 / 2
Lo que carga o incrusta de fuera procede de servicios conocidos y estables (Google Fonts, cdnjs y Tailwind CSS), se encuentra formalmente documentado en la nota de decisiones arquitectónicas (`DECISIONES.md`), y los textos, esquemas vectoriales SVG y datos propios están almacenados dentro del material.

### 5. Accesibilidad — Puntuación: 1 / 2
Se evaluó mediante inspección técnica del DOM y recorrido con teclado: el portal central y aplicaciones clave como `cintia.html`, `app_ruffini_dua.html` y `escape_geometrico.html` cuentan con navegación por teclado, alto contraste y atributos ARIA, aunque en ciertas interacciones complejas de tablas o modales se recomienda continuar reforzando las descripciones auditivas complementarias.

### 6. Material ajeno — Puntuación: 2 / 2
Cada biblioteca y elemento ajeno utilizado cuenta con una licencia de código abierto compatible (MIT, SIL OFL, CC BY 4.0), las ilustraciones son de desarrollo propio en SVG y los créditos de procedencia y licencias están formalizados en la documentación y pies de página.

### 7. Rastro — Puntuación: 2 / 2
El repositorio cuenta con una nota de decisiones de diseño y arquitectura formal (`DECISIONES.md`) que documenta la estructura del catálogo, el inventario de dependencias, el comportamiento sin conexión, la ausencia de analítica y el enfoque DUA adoptado.

### 8. Uso de IA — Puntuación: 2 / 2
Tanto en `README.md` como en el catálogo principal y en los pies de página de los recursos se declara abiertamente el uso de Inteligencia Artificial mediante *vibe coding* con Antigravity CLI y modelos de lenguaje, explicitando la supervisión y validación didáctica realizada por la profesora Silvina Elena Busto en el diseño curricular y las secuencias de aprendizaje.

### 9. Licencia — Puntuación: 2 / 2
El repositorio incluye en su raíz los archivos independientes `LICENSE` (licencia libre MIT / GNU AGPL v3 para el código fuente) y `LICENSE-CONTENT` (Creative Commons CC BY-SA 4.0 para los contenidos didácticos), con menciones y enlaces visibles en el pie de página del catálogo y en cada aplicación.

### 10. Reutilización — Puntuación: 2 / 2
El código de todas las aplicaciones es completamente abierto, modular, no ofuscado y sin empaquetar; además, `README.md` provee una guía clara y estructurada para que cualquier docente pueda agregar nuevas aplicaciones al array interactivo del catálogo.
