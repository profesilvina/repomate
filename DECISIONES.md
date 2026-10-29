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
