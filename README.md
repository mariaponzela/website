# María Ponzela portfolio

This portfolio is a Hugo site. Its structure follows the `jorgeweb` example: page content in `content/`, shared templates in `layouts/`, files copied unchanged in `static/`, and source styles in `assets/`.

## Local development

Install [Hugo Extended](https://gohugo.io/installation/), Node.js, and [Tox](https://tox.wiki/), then run:

```sh
npm ci
tox -e site-serve
```

Open <http://localhost:1313>. Tox provides the same site automation pattern as `jorgeweb`:

| Command | Action |
| --- | --- |
| `tox -e site-html` | Build the production site in `public/` |
| `tox -e site-serve` | Serve it at <http://localhost:1313> |
| `tox -e site-debug` | Serve with full renders and caches disabled |
| `tox -e site-clean` | Remove the generated `public/` directory |

Pass extra Hugo flags after `--`, for example `tox -e site-html -- --verbose`. The npm scripts remain available as `npm run dev` and `npm run build`.

## Structure

| Path | Purpose |
| --- | --- |
| `content/_index.html` | Homepage |
| `content/*.html` | Work, about, explorations, and contact pages |
| `content/projects/*.html` | Case studies |
| `layouts/_default/` and `layouts/partials/` | Shared page frame, navigation, metadata, and footer |
| `layouts/404.html` | Not-found page and redirects from old page names |
| `assets/scss/main.scss` | Site styles, compiled by Hugo Extended, then processed by PostCSS |
| `static/assets/` | Images, video, and PDFs |
| `static/CNAME` | Custom domain for GitHub Pages |
| `tox.ini` | Build, serve, debug, and clean automation |

Page URLs remain `/work.html`, `/about.html`, `/gallery.html`, `/contact.html`, and `/projects/<name>.html`. Edit a page's HTML in its content file. The YAML front matter at the top holds page metadata and footer text and links. The header and stylesheet are maintained once in their respective templates and SCSS file.

The GitHub Actions workflow builds on pushes to `main` and publishes `public/` to the `gh-pages` branch. Configure GitHub Pages to serve that branch from its root.
