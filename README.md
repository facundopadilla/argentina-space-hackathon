# Argentina Space — Sitio del Hackathon

Repositorio standalone del sitio del hackathon de Argentina Space, extraído del
monorepo principal para despliegue independiente en Vercel.

## Estructura

- `index.html`, `reglamento.html`, `codigo-de-conducta.html` — páginas del sitio (raíz del repo).
- `assets/` — imágenes, logos, sponsors, librerías vendoreadas (GSAP, Lenis) y CSS compilado.
- `design-system/tokens.css` — tokens del design system (Tailwind CSS v4), fuente del sitio.
- `app.css` — entrada de Tailwind que importa los tokens y define las rutas de detección de clases.

## Preview local

El sitio es HTML/CSS/JS estático servido desde la raíz del repo. Cualquier
servidor estático sirve:

```bash
python3 -m http.server 8000
```

Luego abrir `http://localhost:8000/`.

## Rebuild del CSS

El CSS compilado (`assets/site.css`) ya está commiteado, pero si se modifican
las páginas HTML o `design-system/tokens.css` hay que regenerarlo:

```bash
npm install
npm run build:css
```

## Deploy en Vercel

Sitio estático, sin build step necesario para el deploy: el CSS compilado ya
está en el repo. `vercel.json` habilita `cleanUrls`.

## Pendientes

El HTML contiene marcadores `TODO(...)` y `SLOT(...)` con contenido interino
que falta confirmar o completar (inscripción vía Luma, video del hero, jurado,
premios, agenda, FAQ, política de privacidad, etc.). Buscarlos con:

```bash
grep -rn "TODO(\|SLOT(" *.html
```

También falta definir la URL absoluta de `og:image` una vez exista un dominio
publicado (marcado como `TODO(og)` en `index.html`).

El video del hero (`assets/video/hero-loop.mp4` y `.webm`) todavía no existe;
el directorio solo tiene un `.gitkeep`.
