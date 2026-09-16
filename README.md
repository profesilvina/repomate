# 📐 Repositorio apps de Matemática

Colección de herramientas, mediadores didácticos y aplicaciones interactivas diseñadas para potenciar la enseñanza y el aprendizaje significativo de la matemática en el nivel secundario y superior.

Desarrollado y coordinado por la **Prof. Silvina Busto**.

---

## 🚀 Vista Previa y Acceso Rápido

El repositorio está diseñado como un catálogo dinámico y responsivo, listo para ser publicado en **GitHub Pages**.

- 🌐 **Plataforma:** Aplicación web estática (Vanilla JavaScript, HTML5 semántico, CSS3 moderno y gráficos vectoriales SVG).
- 🔍 **Buscador en tiempo real:** Filtrado instantáneo por conceptos, temas matemáticos, palabras clave y etiquetas.
- 🎛️ **Filtros temáticos:** Clasificación por Nivel Educativo (Secundaria, Superior, Formación Docente) y Eje Temático.
- ♿ **Herramientas de accesibilidad:** Modificador dinámico del tamaño de tipografía (A-, A, A+) y modo de alto contraste.

---

## 🧮 Catálogo de Aplicaciones Incluidas

| Aplicación | Eje Temático | Nivel | Descripción |
| :--- | :--- | :--- | :--- |
| **➗ Mediador Didáctico: Regla de Ruffini** | Álgebra y Polinomios | Secundaria | Andamiaje interactivo casilla a casilla para la división de polinomios con impulsos socráticos, pistas graduadas y ayudas interactivas. |
| **🧮 Calculadora y Algoritmo de Ruffini** | Álgebra y Polinomios | Secundaria | Resolución procedimental paso a paso del método tradicional de Ruffini con reconstrucción del cociente y cálculo del resto. |
| **⚖️ Actividad Interactiva: Tablas de Verdad** | Lógica Proposicional | Superior / Terciario | Entorno de resolución, autoevaluación y clasificación de tablas lógicas (Tautología, Contradicción y Contingencia) para 2 y 3 variables con puntaje. |
| **🎨 Arte y Matemática: Explorador Didáctico SVG** | Geometría y Trigonometría | Secundaria | Laboratorio STEAM que aborda proporciones, simetría, teselaciones y transformaciones geométricas mediante arte vectorial interactivo con cuadrícula e inspección de código. |

---

## 📂 Estructura del Repositorio

```text
repoapps_mate/
│
├── index.html                   # Catálogo principal con buscador, filtros y renderizado dinámico
├── app_ruffini_dua.html         # Mediador socrático interactivo de Ruffini
├── ruffini.htm                  # Calculadora algorítmica de Ruffini paso a paso
├── actividad_tablas_verdad.html # Laboratorio interactivo de Tablas de Verdad
├── arte_matematica.html         # Galería interactiva STEAM Arte y Geometría en SVG
│
├── gemini-svg parabola.svg      # Gráfico vectorial SVG de parábola
├── gemini-svg ruffini.svg       # Gráfico vectorial SVG de la regla de Ruffini
├── gemini-svg fraccion.svg      # Gráfico vectorial SVG de fracción
├── gemini-svg triangulo.svg     # Gráfico vectorial SVG de trigonometría
│
├── README.md                    # Documentación del proyecto
└── LICENSE                      # Licencia de uso libre y abierto
```

---

## 💻 Instalación y Uso Local

No requiere la instalación de entornos pesados, bases de datos ni dependencias de Node.js.

1. **Clonar o descargar el repositorio:**
   ```bash
   git clone https://github.com/TU-USUARIO/repoapps-mate.git
   ```
2. **Abrir localmente:**
   - Simplemente haz doble clic en `index.html` para abrirlo en cualquier navegador web moderno (Chrome, Firefox, Edge, Safari).
   - O utiliza la extensión *Live Server* de Visual Studio Code para previsualizarlo en un servidor local.

---

## 🌐 Publicación en GitHub Pages

Para publicar este catálogo online de forma gratuita y accesible para toda la comunidad docente y estudiantil:

1. Sube el proyecto a tu repositorio de GitHub.
2. Ve a **Settings** (Configuración) > **Pages**.
3. En **Branch**, selecciona la rama `main` (o `master`) y la carpeta `/ (root)`.
4. Haz clic en **Save**. En pocos minutos, tu sitio estará activo en:
   `https://TU-USUARIO.github.io/repoapps-mate/`

---

## ➕ ¿Cómo agregar una nueva aplicación al catálogo?

Para incorporar una nueva herramienta interactiva al repositorio:

1. Coloca el archivo HTML de tu aplicación en la carpeta raíz (por ejemplo, `mi_nueva_app.html`).
2. Abre `index.html` y localiza el array `REPOSITORIO_MATE` en la etiqueta `<script>`.
3. Agrega un nuevo objeto con los siguientes atributos:

```javascript
{
  id: "mate-5",
  emoji: "📐",
  titulo: "Título de la Nueva Aplicación",
  autor: "Nombre del Autor/a",
  descripcion: "Síntesis clara de la propuesta didáctica y los conceptos que aborda.",
  nivel: "Secundaria", // Opciones: "Secundaria", "Superior", "Formación Docente"
  materia: "Matemática",
  eje: "Funciones y Análisis", // Opciones: "Álgebra y Polinomios", "Geometría y Trigonometría", "Lógica Proposicional", "Funciones y Análisis", etc.
  color: "#0284c7", // Color hexadecimal para el borde y botones de la ficha
  url: "mi_nueva_app.html",
  tags: ["Funciones", "Gráficos", "Interactiva"]
}
```

El buscador y los filtros reconocerán y renderizarán automáticamente la nueva ficha sin necesidad de modificar el HTML.

---

## 📄 Licencia

Este repositorio se distribuye bajo la licencia **MIT**.

Eres libre de utilizar, compartir, adaptar y enriquecer estas herramientas didácticas, siempre que se reconozca la autoría original. Para proyectos educativos sin fines de lucro, también se promueve el licenciamiento **Creative Commons Atribución-CompartirIgual 4.0 Internacional (CC BY-SA 4.0)**.

---

## 👩‍🏫 Autoría y Contacto

- **Coordinación y Autoría:** Prof. Silvina Busto
- **Especialidad:** Matemática y Tecnologías Educativas
- **Contacto:** profesilvina@gmail.com
