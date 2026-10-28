# Desarrollo de Software III — Material de clases

Sitio estático con el material teórico-práctico de la materia **Desarrollo de
Software III** (Licenciatura en Sistemas, Universidad John F. Kennedy).
Incluye la clase de presentación y una clase por cada unidad del programa,
desde los orígenes de HTML hasta el desarrollo responsivo con CSS.

- **Sitio**: HTML5 + una única hoja de estilos CSS, sin build y sin JavaScript.
- **Publicación**: GitHub Pages, directamente desde la raíz de la rama `main`.
- **Accesibilidad**: HTML semántico, navegación por teclado, contraste AA y
  respeto por `prefers-reduced-motion`.

## Estructura

```text
.
├── index.html                     Clase 0: presentación, programa y bibliografía
├── clases/
│   ├── 01-origenes-y-evolucion-de-html/
│   │   ├── index.html
│   │   └── ejemplos/              Demos autocontenidos de la clase
│   ├── 02-estructura-de-un-documento-html/
│   ├── 03-etiquetas/
│   ├── 04-control-de-texto/
│   ├── 05-enlaces/
│   ├── 06-tablas/
│   ├── 07-formularios/
│   ├── 08-marcos/
│   └── 09-css-y-responsive/
├── assets/
│   ├── css/curso.css              Única hoja de estilos del sitio
│   └── img/                       Favicon y diagramas
├── docs/
│   ├── README.md                  Guía de mantenimiento
│   └── adr/                       Registros de decisiones de arquitectura
└── .nojekyll
```

Todas las rutas son relativas, de modo que el sitio funciona igual en local,
en `usuario.github.io/repo/` o en un dominio propio.

## Ver el sitio en local

Alcanza con abrir `index.html` en el navegador. Para probar rutas y enlaces
como en producción, serví la carpeta con un servidor estático:

```bash
python3 -m http.server 8000
```

Luego abrí <http://localhost:8000>.

## Publicar en GitHub Pages

1. Crear un repositorio en GitHub y subir este proyecto a la rama `main`.
2. Ir a **Settings → Pages**.
3. En *Build and deployment*, elegir **Deploy from a branch**.
4. Seleccionar la rama `main` y la carpeta `/ (root)`.
5. Guardar. GitHub publica el sitio en `https://<usuario>.github.io/<repo>/`.

El archivo `.nojekyll` evita que GitHub procese el sitio con Jekyll.

## Agregar o editar una clase

1. Duplicar la carpeta de una clase existente y renombrarla con el esquema
   `NN-tema-en-minusculas`.
2. Actualizar en `index.html` el título, el `meta name="description"`, la
   etiqueta de clase, los enlaces anterior/siguiente y el ítem del índice.
3. Agregar la entrada en la portada (`index.html`) y en el riel de clases de
   todas las páginas (el `<nav class="rail">`).
4. Si la clase tiene ejemplos, dejarlos en `ejemplos/` como documentos HTML
   autocontenidos, con su propio `<style>`, para que el alumnado pueda
   copiarlos y abrirlos por separado.

## Convenciones de contenido

- Español rioplatense, sin voseo forzado en los textos institucionales.
- Cada clase incluye: objetivos, desarrollo con ejemplos, errores comunes,
  actividad práctica, resumen y bibliografía del tema.
- Los ejemplos deben funcionar sin conexión y sin dependencias externas.
- Los enlaces externos se abren en la misma pestaña salvo que haya una razón
  concreta para usar `target="_blank"` (y en ese caso, `rel="noopener"`).
- No se inventan números de página ni citas: se referencia la obra y el
  capítulo cuando se conoce.

## Verificación antes de publicar

- Validar el HTML con [Nu Html Checker](https://validator.w3.org/nu/).
- Revisar los enlaces internos y las rutas de los ejemplos.
- Probar a 360 px, 768 px y 1280 px de ancho.
- Recorrer la página solo con teclado y comprobar el foco visible.
- Ejecutar Lighthouse o axe DevTools sobre la portada y una clase.

## Documentación

- [Guía de mantenimiento](docs/README.md)
- [ADR 0001 — Sitio estático con HTML y CSS](docs/adr/0001-sitio-estatico-html-css/README.md)

## Créditos

Material elaborado para la cátedra de Desarrollo de Software III. El programa
de la materia se conserva en `docs/programa/` para referencia.
