# Música — bajo y batería

Sitio personal de estudio. Las reglas del proyecto están en [CLAUDE.md](CLAUDE.md).

## Ver el sitio

Necesita un servidor estático (el sitio lee `contenido.json` y los `.md` con `fetch`,
que no funciona abriendo el archivo directo desde el disco):

```
python -m http.server 8000
```

Y abrir <http://127.0.0.1:8000>.

## Agregar material

Dos pasos, siempre:

1. Crear el `.md` dentro de `contenido/` (markdown plano, sin front matter).
2. Agregar una línea en `contenido.json`.

```json
{ "archivo": "bajo/clases/2026-08-12-modos.md", "titulo": "Modos sobre vamps", "fecha": "2026-08-12" }
```

Campos posibles: `archivo`, `titulo`, `descripcion`, `fecha`, `semana` (ubica el
archivo en la grilla del curso) y `vertical: true` (para videos filmados en vertical).

Una semana del curso puede traer `dias`: una lista de clases, una por día, cada una
en su propio `.md`. La página de la semana las muestra como botones y cada clase se
abre sola, con botones de día anterior y siguiente.

```json
{ "archivo": "bajo/curso/semana-02.md", "titulo": "Semana 2 — …", "semana": 2,
  "dias": [
    { "archivo": "bajo/curso/semana-02/dia-1.md", "titulo": "Día 1 — …" }
  ] }
```

Una URL de YouTube sola en su renglón se convierte en reproductor. No se escribe HTML.

## Estructura

```
index.html          Shell único, ruteo por hash
contenido.json      Índice de todo el contenido
contenido/          El material, en markdown
css/                Estilos + fuentes autoalojadas
js/                 app.js (ruteo y render), lib/marked.min.js
herramientas/       Herramientas interactivas — no se tocan
```
