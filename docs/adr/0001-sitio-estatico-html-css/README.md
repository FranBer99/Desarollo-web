# ADR 0001 — Sitio estático con HTML y CSS, sin build

- **Estado**: aceptado
- **Fecha**: 2026-10-28

## Contexto

El material de la materia **Desarrollo de Software III** debe publicarse en
GitHub Pages para que el alumnado lo consulte desde cualquier dispositivo.
El contenido es teórico-práctico y el propio sitio funciona como ejemplo de
las buenas prácticas que se enseñan: HTML semántico, CSS en una hoja externa,
accesibilidad y diseño responsivo.

El sitio de referencia de la cátedra (*Maquetación y Desarrollo Web*) usa
pandoc para convertir Markdown en HTML y Tailwind compilado. Ese flujo agrega
dos dependencias de build, genera HTML que no se edita a mano y obliga a
instalar herramientas para publicar.

## Decisión

Construir el sitio con **HTML5 y CSS puros**, sin paso de compilación:

- Una carpeta por clase con un `index.html` escrito a mano.
- Una única hoja de estilos compartida, `assets/css/curso.css`.
- Ejemplos autocontenidos en `clases/NN-tema/ejemplos/`.
- Sin JavaScript: la navegación, el índice lateral y los ejemplos embebidos
  se resuelven con HTML y CSS nativos.
- Publicación directa desde la raíz de `main` con GitHub Pages y `.nojekyll`.

## Alternativas consideradas

1. **Markdown + pandoc**, como el sitio de referencia. Cómodo para escribir,
   pero requiere instalar pandoc para publicar, el HTML resultante es
   generado y no se corresponde con lo que se muestra en el curso.
2. **Tailwind compilado**. Agrega Node, un paso de build y clases utilitarias
   que dificultan explicar la cascada y la especificidad en clase.
3. **Framework de aplicación (React, Astro, etc.)**. Innecesario para
   contenido estático y contrario al objetivo didáctico de mostrar HTML y CSS
   sin capas intermedias.

## Consecuencias

### Positivas

- Publicar es copiar archivos: no hay dependencias ni versiones que mantener.
- El código fuente del sitio es, a la vez, material de estudio.
- Funciona sin conexión y sin JavaScript.
- Las rutas relativas permiten mover el sitio de repositorio o dominio sin
  cambios.

### Negativas

- El encabezado, el riel de clases y el pie se repiten en cada página; un
  cambio global requiere editar todos los archivos.
- No hay plantillas ni validación automática de enlaces en el repositorio.
- El contenido largo se escribe directamente en HTML, con más verbosidad que
  Markdown.

### Mitigaciones

- La estructura de página es uniforme y está documentada en `docs/README.md`.
- Antes de publicar se valida el HTML y se revisan los enlaces internos.
- Si en el futuro el mantenimiento se vuelve costoso, se puede adoptar un
  generador estático sin cambiar las URLs ni el diseño; esta decisión se
  revisaría en un ADR nuevo.
