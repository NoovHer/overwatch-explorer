# 🎮 Roadmap — Overwatch Hero Explorer

> Proyecto colaborativo para aprender Git, Vanilla JS, React y hacer deploy en Vercel.
> Hecho para dos personas trabajando al mismo ritmo.

---

## Fase 0 — Preparación y herramientas
> ⏱ Día 1, unas 2 horas

### Lo que instalan ambos
- [ ] **VS Code** — el editor principal
- [ ] Extensión **Live Share** — para programar juntos en tiempo real
- [ ] Extensión **Prettier** — formatea el código igual para los dos automáticamente
- [ ] Extensión **GitLens** — para ver quién escribió qué línea
- [ ] Extensión **ESLint** — detecta errores lógicos y malas prácticas antes de que exploten
- [ ] **Node.js** versión LTS desde [nodejs.org](https://nodejs.org)
- [ ] **Git** desde [git-scm.com](https://git-scm.com) y configurar nombre y email con `git config`

### Configuración de ESLint
Instalar con una configuración mínima y preestablecida — no configurarlo desde cero:
```bash
npm init @eslint/config
```
Elegir: `problems only` → `JavaScript modules` → `browser`. Listo. No tocar más por ahora.

> 💡 **Prettier vs ESLint:** Prettier arregla el formato visual (espacios, comas, saltos de línea). ESLint detecta errores lógicos — variables sin usar, `return` olvidados, constantes reasignadas. Se complementan, no se reemplazan.

### Cuentas que necesitan
- [ ] Cuenta en **GitHub** — donde va a vivir el código
- [ ] Cuenta en **Vercel** — donde van a hacer el deploy, conectada a GitHub

### Documentación clave
- [GitHub Docs](https://docs.github.com)
- [OverFast API](https://overfast-api.tekrop.fr)
- [VS Code Docs](https://code.visualstudio.com/docs)
- [ESLint — primeros pasos](https://eslint.org/docs/latest/use/getting-started)

---

## Fase 1 — Git y GitHub en equipo
> ⏱ 3 días

### Conceptos que deben dominar
- [ ] **Repositorio** — la carpeta del proyecto con todo su historial
- [ ] **Commit** — una foto del código en un momento, siempre con mensaje descriptivo
- [ ] **Rama (branch)** — una copia paralela para trabajar sin afectar lo que ya funciona
- [ ] **Push / Pull** — subir y bajar cambios de GitHub
- [ ] **Pull Request (PR)** — propuesta de mergear una rama, el otro la revisa antes
- [ ] **Merge** — unir los cambios de una rama a `main`
- [ ] **Conflicto** — cuando dos personas editaron la misma línea, Git avisa y se resuelve juntos

### Flujo de trabajo que van a usar siempre
- [ ] Uno crea el repo en GitHub, el otro hace `git clone URL`
- [ ] Para cada feature: `git checkout -b nombre-feature`
- [ ] Trabajan, guardan: `git add .` → `git commit -m "tipo: descripción"`
- [ ] Suben: `git push origin nombre-feature`
- [ ] Abren un Pull Request en GitHub, el otro lo revisa y aprueba
- [ ] Mergean a `main` — Vercel hace deploy automático

> 💡 **Regla de oro:** nunca pusheen directo a `main`. Siempre rama → PR → merge. Aunque sea un cambio pequeño.

### Commits semánticos (Conventional Commits)
Adopten este estándar desde el día uno — es lo que usan equipos profesionales y hace el historial del repo mucho más legible.

| Tipo | Cuándo usarlo | Ejemplo |
|---|---|---|
| `feat:` | Nueva funcionalidad | `feat: agregar filtro por rol de héroe` |
| `fix:` | Corregir un bug | `fix: corregir renderizado de imagen rota` |
| `docs:` | Documentación o README | `docs: actualizar README con link de Vercel` |
| `style:` | Cambios visuales, CSS | `style: aplicar paleta de colores a las cards` |
| `refactor:` | Mejorar código sin cambiar lo que hace | `refactor: extraer fetch a api.js` |
| `chore:` | Configuración, dependencias | `chore: configurar ESLint y Prettier` |

### Práctica concreta
- [ ] Cada quien crea un archivo con su nombre en el repo y hace un PR con commit semántico
- [ ] Provoquen un conflicto a propósito editando la misma línea — resuélvanlo juntos
- [ ] Configurar en GitHub: Settings → Branches → requerir PR antes de merge a `main`

### Documentación
- [Learn Git Branching (interactivo)](https://learngitbranching.js.org/?locale=es_AR)
- [GitHub: primeros pasos](https://docs.github.com/es/get-started)
- [Pro Git — libro gratis en español](https://git-scm.com/book/es/v2)
- [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/)

---

## Fase 2 — Moodboard y diseño base
> ⏱ 1 día

### ¿Qué es un moodboard?
Un moodboard es una colección de imágenes, colores y referencias visuales que definen cómo se va a ver el proyecto. Se hace **antes de escribir una línea de CSS**. Evita pasar horas cambiando colores sin decidirse — se decide una vez aquí.

### Cómo hacerlo paso a paso
- [ ] Entrar a **Dribbble** y buscar: `game card UI`, `hero card dark`, `overwatch fan page`
- [ ] Guardar 4 o 5 capturas que les gusten — no tienen que ser perfectas, solo inspiración
- [ ] De esas capturas, anotar: ¿qué colores dominan? ¿es oscuro o claro? ¿qué tipografía?
- [ ] Elegir **una paleta de 3 colores**: fondo, acento principal, texto
- [ ] Elegir **una fuente** — Google Fonts tiene opciones gratuitas como Rajdhani o Barlow Condensed
- [ ] Definir cómo se ve una card: ¿tiene imagen del héroe? ¿su rol? ¿su nombre?

### Lo que deben tener definido al terminar esta fase
- [ ] Paleta de colores con sus códigos hex
- [ ] Tipografía elegida e importada de Google Fonts
- [ ] Un boceto (papel o digital) de la lista de héroes y la vista de detalle

> 💡 **Herramienta útil:** [coolors.co](https://coolors.co) para generar paletas. Escriben un color base y sugiere combinaciones que funcionan.

### Herramientas
- [Dribbble — referencias de diseño](https://dribbble.com/search/hero-card-ui)
- [Coolors — paletas de color](https://coolors.co)
- [Google Fonts](https://fonts.google.com)
- [Figma — bocetos digitales (gratis)](https://www.figma.com)

---

## Fase 3 — Versión Vanilla JS
> ⏱ 1 a 2 semanas

### Estructura de archivos
```
proyecto-vanilla/
├── index.html       → estructura base con un div#app donde va todo
├── style.css        → todos los estilos, usando las variables del moodboard
└── js/
    ├── api.js       → solo las funciones que hablan con la API
    ├── render.js    → funciones que crean HTML a partir de los datos
    └── main.js      → punto de entrada, estado central y conexión entre archivos
```

### ES Modules — la forma correcta de conectar los archivos
El error más común es usar `<script>` normales para cada archivo, lo que contamina el ámbito global y mezcla todas las variables entre sí.

La forma correcta en `index.html`:
```html
<!-- Solo un script, con type="module" -->
<script type="module" src="js/main.js"></script>
```

Y entre archivos, usar `export` e `import`:
```js
// api.js
export async function fetchHeroes() { ... }

// main.js
import { fetchHeroes } from './api.js';
```

> 💡 **Por qué importa:** esto aísla el código por archivo y es exactamente cómo funciona la importación de componentes en React. Cuando migren, el concepto ya va a ser familiar.

### Separación de estado y vista
Antes de llegar a `useState` en React, apliquen el concepto de estado en Vanilla. La mala práctica es leer datos directamente del DOM para saber qué filtrar.

La forma correcta es tener un objeto central en `main.js` como única fuente de verdad:
```js
// main.js — el estado vive aquí, nadie más lo modifica directamente
let state = {
  heroes: [],
  filter: 'all',
  search: ''
};

// Cada vez que ocurre un evento, primero actualizan el estado...
function setFilter(role) {
  state.filter = role;
  render(state); // ...y luego llaman a render con el estado actualizado
}
```

> 💡 **Comparación directa:** este objeto `state` es exactamente lo que después van a manejar con `useState` en React. La lógica es idéntica, solo cambia la sintaxis.

### Manejo defensivo de errores — desde el primer fetch
No dejen el manejo de errores para el final. Desde el primer `fetch` en `api.js`:
```js
export async function fetchHeroes() {
  try {
    const response = await fetch('https://overfast-api.tekrop.fr/heroes');

    if (!response.ok) {
      throw new Error(`Error ${response.status}: no se pudo cargar la lista de héroes`);
    }

    return await response.json();
  } catch (error) {
    // Lanzar el error para que main.js lo capture y render.js lo muestre en pantalla
    throw error;
  }
}
```

> 💡 **Por qué `response.ok`:** `fetch` no lanza errores automáticamente por respuestas 404 o 500. Sin esta verificación, un error de la API pasa desapercibido y el código falla de formas raras más adelante.

### Features en orden — una por rama de Git
- [ ] **Feature 1:** fetch de héroes y mostrarlos en pantalla como cards básicas
- [ ] **Feature 2:** aplicar los estilos del moodboard a las cards
- [ ] **Feature 3:** filtro por rol con botones (Tank / Damage / Support)
- [ ] **Feature 4:** buscador por nombre en tiempo real
- [ ] **Feature 5:** vista de detalle con habilidades al hacer click en una card
- [ ] **Feature 6 (extra):** favoritos guardados en `localStorage`

### Conceptos JS que van a usar y reforzar
- [ ] `fetch` + `async/await` + `try/catch` para traer los datos de la API de forma segura
- [ ] `Array.map()`, `filter()` para transformar y filtrar héroes desde el estado
- [ ] `innerHTML` y `createElement` para construir el DOM desde `render.js`
- [ ] `addEventListener` para clicks, inputs y eventos
- [ ] ES Modules — `export` e `import` entre archivos
- [ ] Estado centralizado — leer del estado, nunca del DOM
- [ ] `localStorage` para guardar favoritos sin backend

### Etiquetas semánticas de HTML
En lugar de construir todo con `<div>`, usen etiquetas que describen el contenido:
```html
<header>     → barra superior con título y buscador
<main>       → contenido principal de la página
<article>    → cada card de héroe es un artículo independiente
<section>    → para agrupar la lista o el área de filtros
<nav>        → los botones de filtro por rol
```

> 💡 **Por qué importa:** las etiquetas semánticas mejoran la accesibilidad, el SEO y hacen el HTML más fácil de leer. Es un hábito que cuesta nada adoptar desde el inicio.

### Documentación
- [MDN — Fetch API](https://developer.mozilla.org/es/docs/Web/API/Fetch_API)
- [MDN — ES Modules](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Modules)
- [MDN — DOM](https://developer.mozilla.org/es/docs/Web/API/Document_Object_Model)
- [OverFast API docs](https://overfast-api.tekrop.fr)
- [MDN — localStorage](https://developer.mozilla.org/es/docs/Web/API/Window/localStorage)

---

> ✦ **Punto de migración** — la app Vanilla funciona completa → ahora la reescriben en React con todo lo que aprendieron ✦

---

## Fase 4 — Migración a React + Vite
> ⏱ 1 a 2 semanas

### Setup inicial
- [ ] Repo nuevo en GitHub — el proyecto Vanilla queda intacto como referencia
- [ ] Crear proyecto: `npm create vite@latest` → elegir React → JavaScript
- [ ] Instalar React Router: `npm install react-router-dom`
- [ ] Instalar Tailwind CSS siguiendo su guía oficial para Vite
- [ ] Conectar el repo nuevo a Vercel desde el primer día

### Estructura de componentes
```
src/
├── App.jsx                     → componente raíz, maneja las rutas
├── components/
│   ├── HeroCard.jsx            → card de un héroe, recibe props
│   ├── HeroList.jsx            → lista de cards, maneja el fetch
│   ├── SearchBar.jsx           → input de búsqueda
│   └── FilterBar.jsx           → botones de rol
├── pages/
│   └── HeroDetail.jsx          → página de detalle con React Router
└── services/
    └── api.js                  → el mismo fetch de Vanilla, reutilizado
```

### Conceptos que van a aprender aquí
- [ ] **JSX** — HTML dentro de JavaScript, la sintaxis de React
- [ ] **Props** — cómo pasarle datos a un componente hijo
- [ ] **useState** — el estado local de un componente (el mismo concepto del objeto `state` de Vanilla)
- [ ] **useEffect** — ejecutar el fetch cuando el componente carga
- [ ] **React Router** — `Link` para navegar, `useParams` para leer la URL
- [ ] **Lifting state up** — subir el estado al padre cuando dos hijos lo necesitan

> 💡 **Comparación directa con Vanilla:**
> - `render.js` → componentes
> - objeto `state` → `useState`
> - `addEventListener` → `onChange` / `onClick`
> - `import` de ES Modules → `import` de componentes
>
> Es la misma lógica, diferente forma. Van a entenderlo inmediatamente porque ya lo vivieron.

### Documentación
- [React — documentación oficial en español](https://es.react.dev/learn)
- [Vite — guía oficial](https://vitejs.dev/guide/)
- [React Router docs](https://reactrouter.com/en/main)
- [Tailwind CSS docs](https://tailwindcss.com/docs)

---

## Fase 5 — Deploy y pulido final
> ⏱ 2 a 3 días

### Deploy en Vercel
- [ ] Ir a vercel.com → Add New Project → importar el repo de GitHub
- [ ] Vercel detecta Vite automáticamente — solo hacer click en Deploy
- [ ] Cada push a `main` hace deploy automático — la URL siempre actualizada
- [ ] Consiguen una URL tipo `su-proyecto.vercel.app` para compartir

### Pulido que vale la pena hacer
- [ ] **Loading state** — spinner o skeleton mientras carga la API
- [ ] **Error state** — mensaje amigable en pantalla si la API falla (no solo en consola)
- [ ] **Empty state** — mensaje si la búsqueda no encuentra nada
- [ ] **Responsive** — que se vea bien en celular y desktop
- [ ] **Favicon y título** — detalles que hacen que se vea terminado
- [ ] **README en GitHub** — descripción, screenshot y link a Vercel

### Accesibilidad (a11y) — checklist de pulido
- [ ] Verificar que toda la app sea navegable con la tecla `Tab`
- [ ] Los botones de filtro con solo iconos deben tener `aria-label` descriptivo
- [ ] Las imágenes de héroes deben tener atributo `alt` con el nombre del héroe
- [ ] Contrastar colores — el texto debe ser legible sobre el fondo elegido

> 💡 **El README importa:** si algún día muestran este proyecto, es lo primero que ve alguien. Una buena descripción y un screenshot hacen una gran diferencia.

### Documentación
- [Vercel docs](https://vercel.com/docs)
- [Cómo escribir un buen README](https://docs.github.com/es/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)
- [MDN — Accesibilidad web](https://developer.mozilla.org/es/docs/Learn/Accessibility)

---

## Resumen del stack

| Herramienta | Para qué |
|---|---|
| Git + GitHub | Control de versiones y trabajo en equipo |
| Conventional Commits | Historial de cambios claro y profesional |
| VS Code + Live Share | Editor y programación colaborativa |
| Prettier + ESLint | Formato consistente y detección de errores |
| Vanilla JS + ES Modules | Primera versión, repasar fundamentos |
| React + Vite | Segunda versión, estructura de componentes |
| Tailwind CSS | Estilos rápidos y profesionales |
| React Router | Navegación entre páginas sin recargar |
| OverFast API | Datos de héroes, habilidades y perks |
| Vercel | Deploy automático conectado a GitHub |

---

## API de referencia — OverFast

Base URL: `https://overfast-api.tekrop.fr`

| Endpoint | Descripción |
|---|---|
| `GET /heroes` | Lista de todos los héroes |
| `GET /heroes/:key` | Detalle de un héroe (habilidades, perks, lore) |
| `GET /heroes?role=tank` | Filtrar por rol: `tank`, `damage`, `support` |

---

*Roadmap generado como guía de aprendizaje para el proyecto Overwatch Hero Explorer.*
