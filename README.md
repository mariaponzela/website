# Portafolio de María Ponzela

## Acerca de

Este portafolio presenta el trabajo de María Ponzela. Está construido con Hugo.
El contenido de las páginas vive en `content/`, las plantillas compartidas en
`layouts/`, los estilos fuente en `assets/` y los archivos que se copian sin
cambios en `static/`.

## Primeros pasos

Instala [Hugo Extended](https://gohugo.io/installation/), Node.js y
[Tox](https://tox.wiki/). Después, desde la raíz del proyecto, ejecuta:

```sh
npm ci
tox -e site-serve
```

Abre <http://localhost:1313> para ver el sitio. También puedes iniciarlo con
`npm run dev`.

## Guía de uso

Las páginas principales están en `content/_index.html` y `content/*.html`; los
casos de estudio están en `content/projects/*.html`. Edita el HTML de cada
archivo para cambiar su contenido. El bloque YAML inicial contiene los
metadatos de la página y los textos y enlaces del pie de página.

Las rutas públicas son `/work.html`, `/about.html`, `/gallery.html`, `/contact.html` y `/projects/<nombre>.html`. Coloca imágenes, vídeos y documentos en `static/assets/` y enlázalos desde las páginas. La navegación y el pie de página compartidos están en `layouts/partials/`.

## Desarrollo

| Comando | Acción |
| --- | --- |
| `tox -e site-html` | Genera el sitio de producción en `public/` |
| `tox -e site-serve` | Inicia el servidor local en <http://localhost:1313> |
| `tox -e site-debug` | Inicia el servidor con renderizado completo y sin caché |
| `tox -e site-clean` | Elimina el directorio generado `public/` |

Puedes pasar opciones adicionales a Hugo después de `--`, por ejemplo `tox -e
site-html -- --verbose`. También está disponible `npm run build`.

Los estilos se editan en `assets/scss/main.scss`; Hugo Extended los compila y
PostCSS los procesa. La plantilla de la página 404 y las redirecciones de rutas
antiguas están en `layouts/404.html`.

El workflow de GitHub Actions publica `public/` en la rama `gh-pages`
únicamente cuando se crea una etiqueta con el formato `vX.Y.Z`, donde `X`, `Y`
y `Z` son números enteros (por ejemplo, `v1.2.3`). Configura GitHub Pages para
servir la raíz de esa rama.
