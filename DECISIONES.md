# Nota de decisiones de diseño y arquitectura (ADR)
> **Proyecto:** Repositorio de aplicaciones de matemática (`repoapps_mate`)  
> **Fecha de redacción:** Octubre de 2026 *(Redactada con posterioridad a la creación inicial para documentar formalmente las decisiones técnicas, pedagógicas y éticas adoptadas)*.  
> **Coordinación y desarrollo:** Prof. Silvina Elena Busto (EDI: Matemática y el trabajo por proyectos - ISFDyT N° 24)  
> **Asistencia de IA:** Antigravity CLI & Google Gemini  

---

## 1. Contexto y propósito pedagógico

El repositorio `repoapps_mate` tiene como propósito compilar, catalogar y poner a disposición abierta de la comunidad educativa una colección de herramientas interactivas, mediadores didácticos y aplicaciones creadas mediante *vibe coding* (programación asistida por lenguaje natural e inteligencia artificial). Las aplicaciones abordan contenidos curriculares clave de matemática para la educación secundaria y superior (álgebra, polinomios, lógica proposicional, geometría plana, magnitudes en cuerpos tridimensionales, modelado STEAM en SVG fracciones equivalentes, resolución de problemas con porcentajes, promedios y consumo de batería en smartphones, y transformaciones geométricas en el plano articuladas con el arte abstracto y la proporción áurea), articuladas bajo el enfoque del Aprendizaje Basado en Proyectos (ABP) y los principios del Diseño Universal para el Aprendizaje (DUA).

---

## 2. Decisiones arquitectónicas y técnicas

### Decisión 1: Arquitectura cliente estático puro (Jamstack / Client-Side)
- **Contexto:** Se requería una solución técnica que cualquier docente o estudiante pudiera abrir, explorar y reutilizar de forma inmediata sin servidores, sin Node.js, sin bases de datos remotas y sin configuraciones complejas.
- **Decisión adoptada:** Cada aplicación es una página web autónoma e independiente (HTML5 semántico, CSS3 moderno y JavaScript vanilla) ejecutable en cualquier navegador moderno.
- **Alternativas descartadas:** Frameworks pesados de frontend con empaquetadores (React/Vue/Webpack) y backends que demandan hosting especializado o bases de datos pagas.
- **Consecuencias:** Máxima portabilidad, compatibilidad total con GitHub Pages, carga ultrarrápida y mantenimiento sencillo para la comunidad docente.

---

### Decisión 2: Inventario de dependencias externas y comportamiento sin conexión (offline)
- **Contexto:** Para optimizar el tiempo de desarrollo y asegurar interfaces claras, modernas e intuitivas, se recurrió a recursos de diseño consolidados.
- **Dependencias externas seleccionadas:**
  - **Google Fonts (CDN):** Tipografías web de libre distribución (*Outfit*, *Space Grotesk*, *Inter*, *VT323*, *Press Start 2P*, *Fira Code*, *Baloo 2*, *Nunito*, *IBM Plex Mono*), licenciadas bajo SIL Open Font License.
  - **FontAwesome Free (cdnjs CDN):** Iconografía vectorial semántica para accesibilidad visual, licenciada bajo CC BY 4.0 / SIL OFL.
  - **Tailwind CSS (CDN en tiempo de ejecución):** Utilizado en [alicia.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/alicia.html) y [escape_geometrico.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/escape_geometrico.html) para estilos utilitarios responsivos, bajo licencia MIT.
  - **GeoGebra deployggb (CDN):** Script oficial https://www.geogebra.org/apps/deployggb.js empleado en [vanina.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/vanina.html) para inyectar applets dinámicos de modelización matemática. Cuenta con aviso de detección y fallback offline para asegurar el funcionamiento autónomo del Escape Room y la Certificación.
- **Comportamiento sin internet:**
  - Si un usuario abre los recursos descargados en un entorno sin conexión a internet, la lógica matemática, los cálculos y los textos continúan funcionando normalmente.
  - Las tipografías se sustituyen automáticamente por las predeterminadas del sistema operativo (*system-ui*, *monospace*).
  - En las aplicaciones con Tailwind CDN, la maquetación visual se simplifica, pero la funcionalidad y el contenido permanecen intactos.
  - Las ilustraciones y modelos geométricos son gráficos vectoriales SVG o Canvas integrados en el código local, por lo que no requieren conexión para visualizarse.

---

### Decisión 3: Privacidad estricta y protección de datos del alumnado
- **Contexto:** En cumplimiento con las directrices de la guía VCER (*vibe coding* educativo responsable) y la legislación de protección de datos personales de estudiantes.
- **Decisión adoptada:**
  - Ninguna aplicación solicita nombres, apellidos ni identificadores personales para su uso en el aula.
  - La única persistencia utilizada es el almacenamiento local del navegador (`localStorage`) en [cintia.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/cintia.html), reservado únicamente a guardar contadores numéricos de misiones y estrellas lúdicas en el dispositivo del estudiante.
  - En [marisa.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/marisa.html) (*Misión Batería*) y [vanina.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/vanina.html) (*Estudio InfinitA*), la asignación de variantes de equipos, estados del Escape Room y respuestas del quiz opera de manera puramente anónima y transitoria en memoria de sesión, sin solicitar nombres propios, correos ni datos identificatorios.
  - Cero analítica de terceros: el código está 100 % libre de Google Analytics, Microsoft Clarity, Meta Pixel o herramientas de rastreo.
  - Cero comunicaciones de red salientes (`fetch`, `XMLHttpRequest`).

---

### Decisión 4: Accesibilidad e inclusión educativa (DUA)
- **Contexto:** Asegurar el acceso equitativo al conocimiento matemático según las Pautas WCAG 2.1 y el Diseño Universal para el Aprendizaje.
- **Decisión adoptada:**
  - El catálogo principal y las aplicaciones interactivas (incluyendo la barra DUA superior de [marisa.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/marisa.html) y [cintia.html](file:///C:/Users/User/Documents/MiWebDocente/EDI2026/repoapps_mate/cintia.html)) incorporan conmutador de **alto contraste** y modificador dinámico de tamaño de tipografía (A-, A, A+).
  - Se incorporan apoyos de síntesis de voz en el navegador mediante la Web Speech API nativa.
  - Navegación completa por teclado con indicadores de foco (`:focus-visible`) y atributos ARIA explícitos (`aria-label`, `aria-live`, `aria-pressed`, `role`) en botones y controles.
  - No dependencia exclusiva del color: los estados de validación matemática (correcto/incorrecto) se acompañan siempre de texto, símbolos e iconos.

---

### Decisión 5: Esquema dual de licenciamiento abierto (software y contenido)
- **Contexto:** Garantizar la soberanía pedagógica y la libertad de reutilización de los materiales por otros docentes.
- **Decisión adoptada:**
  - **Código fuente (software):** Licenciado bajo **GNU AGPL v3 (Affero General Public License)**, garantizando que toda derivación o publicación mantenga el código abierto.
  - **Contenido didáctico y actividades:** Licenciado bajo **Creative Commons Atribución-CompartirIgual 4.0 Internacional (CC BY-SA 4.0)**, permitiendo adaptar, traducir y enriquecer las secuencias citando la autoría original.
---

### Decisión 6: Integración y armonización de las aplicaciones de Verónica Oliva y Karen Salinas
- **Contexto:** Incorporación al catálogo de dos nuevas aplicaciones desarrolladas por cursantes bajo metodología de *Vibe Coding*: «El Gallinero Matemático» (Verónica Oliva) y «Misión Energía: Código Verde — Simulador de Consumo Eléctrico» (Karen Salinas). La app de Karen requirió extracción completa desde la sesión de Gemini y reconstrucción íntegra de su estructura HTML truncada.
- **Decisiones adoptadas:**
  - **Karen Salinas (`karen.html`):** Restauración completa de la estructura HTML semántica a partir del log de Gemini. Integración del motor de síntesis de voz nativo (Web Speech API con voz en español neutro/argentino `es-AR`), gráficos interactivos dinámicos mediante Chart.js, representaciones simultáneas (simbólica, numérica, tabular y gráfica) y barra de accesibilidad DUA con conmutador de alto contraste y escalado tipográfico.
  - **Verónica Oliva (`veronica.html`):** Estandarización de nombre de archivo a minúsculas, incorporación de enlace de retorno al catálogo principal en la barra superior (`topbar`) y pie de página institucional con mención de autoría, accesibilidad DUA y licencia abierta CC BY-SA 4.0.
  - Ambas aplicaciones operan 100 % en el navegador del cliente sin recopilar datos personales, sin analítica invasiva y en total concordancia con las pautas VCER.

---

### Decisión 7: Incorporación masiva y estandarización VCER de nuevas aplicaciones (Noviembre 2026)
- **Contexto:** Incorporación de las aplicaciones de Ángel Viegas, 2da app de Marisa Sierra (afiche digital), Enzo y Alberto (2do año Enseñar con Tecnología), Gabriel D'Amelia y Ana Lía Solores (2do año Enseñar con Tecnología), Fabricio Rebolledo y verificación de los módulos integrados de Vanina Malatesta.
- **Decisiones adoptadas:**
  - **Ángel Viegas (`escaperoonviegas.htm` / `viegas.html`):** «Pioneras de la Geometría y el Enigma del Panal». Se corrigieron problemas de codificación de caracteres y emojis, se incorporó barra de herramientas DUA (conmutador de alto contraste, escalado tipográfico A-/A/A+, síntesis de voz Web Speech API), soporte de teclado con tecla Enter en inputs, retroalimentación acústica sutil mediante Web Audio API y barra visual de progreso formativo (6 estaciones). Licenciamiento dual GNU AGPL v3 y CC BY-SA 4.0 añadido.
  - **Marisa Sierra (`marisa_afiche.html`):** «Creador de Afiches y Flyers – Misión Batería». Se unificó en la misma tarjeta del catálogo institucional (`mate-8`) mediante botones de acción múltiples («Abrir Juego y Simulador» y «Abrir Creador de Afiches / Flyers (2.ª app)»). Se agregó el identificador SPDX GNU AGPL v3, créditos de autoría formal, diseño responsive y pie de página institucional VCER.
  - **Enzo y Alberto (`mision_triangulos.html`):** «Misión Triángulos – Desigualdad Triangular» (2do año Enseñar con Tecnología). Se incorporó identificador SPDX, barra de accesibilidad DUA con síntesis de voz y alto contraste, regiones accesibles `aria-live` para las tres desigualdades simultáneas, consignas formativas ABP y comandos para réplica en GeoGebra Classic.
  - **Gabriel D'Amelia y Ana Lía Solores (`escape_cuerpos_geometricos/index.html`):** «Escape Room: Muestra Virtual de Cuerpos Geométricos» (2do año Enseñar con Tecnología). Proyecto desarrollado en React + TypeScript + Tailwind. Se resolvió la resolución de dependencias peer (`npm install --legacy-peer-deps`), se configuró base relativa en `vite.config.ts`, se incorporaron créditos de autoría formal en la pantalla de bienvenida e información didáctica DGCyE, y se compiló a una carpeta de distribución estática autónoma (`escape_cuerpos_geometricos`) integrable sin servidor.
  - **Fabricio Rebolledo (`fabricio.html` / `el_tiro_perfecto_pro Fabricio.html`):** «El Tiro Perfecto PRO: Laboratorio de Lanzamiento Parabólico». Actualización a la versión PRO entregada por el estudiante. Se integró la nueva interfaz y física con motor de canvas 2D, parábola ideal punteada superpuesta a la trayectoria física con rebotes continuos, cálculo del vértice analítico en tiempo real, 4 misiones de precisión (incluyendo obstáculo/defensor a 2,5 m y 2,7 m de altura), 5 preguntas orientadoras de indagación ABP, barra DUA completa (alto contraste, tipografía A-/A/A+, síntesis de voz Web Speech API) e identificador SPDX GNU AGPL v3 con pie de página VCER.
  - **Vanina Malatesta (`vanina.html`):** Se verificó que la aplicación unificada ya integra íntegramente el contenido de las pestañas 2 (Quiz de certificación nivel 1), 3 (GeoGebra la grilla áurea), 4 (Escape room el cubista con 6 variantes por equipo) y 5 (Libro de GeoGebra integrador con applets dinámicos).
  - Todas las aplicaciones respetan el licenciamiento dual (GNU AGPL v3 para código, CC BY-SA 4.0 para contenidos), operan 100 % en el navegador local sin recopilación de datos identificatorios y declaran formalmente el uso ético de IA con supervisión humana docente.
