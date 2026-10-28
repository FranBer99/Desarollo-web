# Documentación del proyecto

Este directorio reúne la documentación de mantenimiento del sitio de la
materia **Desarrollo de Software III** (Universidad John F. Kennedy).

## Contenido

- [`adr/`](adr/): registros de decisiones de arquitectura (ADR). Cada decisión
  significativa vive en su propia carpeta `NNNN-titulo-breve/` con un
  `README.md` que describe estado, contexto, decisión y consecuencias.
- [`programa/`](programa/): programa analítico de la materia y bibliografía.

## Cómo mantener el sitio

### Editar una clase

Cada clase es un documento HTML independiente en
`clases/NN-tema/index.html`. La estructura mínima es:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Clase NN · Tema — Desarrollo de Software III</title>
    <meta name="description" content="...">
    <link rel="icon" href="../../assets/img/favicon.svg" type="image/svg+xml">
    <link rel="stylesheet" href="../../assets/css/curso.css">
  </head>
  <body>
    <a class="saltar-contenido" href="#contenido">Saltar al contenido</a>
    <!-- encabezado, riel de clases, índice lateral, contenido y pie -->
  </body>
</html>
```

Al agregar una clase hay que actualizar:

1. El riel de clases (`nav.rail`) de **todas** las páginas.
2. El índice de la portada (`index.html`).
3. Los enlaces anterior/siguiente de las clases vecinas.
4. El `<title>` y la `<meta name="description">` de la nueva página.

### Estilo

Toda la presentación vive en `assets/css/curso.css`. No se usan estilos en
línea ni atributos de presentación obsoletos (`align`, `bgcolor`, `border`,
`cellpadding`, `font`). Los componentes disponibles son:

| Componente | Marcado |
| --- | --- |
| Aviso | `<aside class="aviso aviso--nota" aria-label="Nota">` |
| Bloque de código | `<figure class="bloque-codigo"><figcaption>archivo</figcaption><pre><code>…</code></pre></figure>` |
| Tabla | `<div class="tabla"><table>…</table></div>` |
| Ejemplo embebido | `<figure class="demo"><iframe …></iframe><figcaption>…</figcaption></figure>` |
| Ejercicio | `<div class="ejercicio">…</div>` |
| Resumen | `<div class="resumen">…</div>` |
| Bibliografía | `<div class="bibliografia">…</div>` |

### Ejemplos

Los ejemplos de cada clase viven en `clases/NN-tema/ejemplos/`. Deben ser
documentos HTML completos y autocontenidos (con su `<style>` propio), sin
dependencias externas, para que el alumnado pueda abrirlos, copiarlos y
modificarlos.

Se embeben en la clase con un `iframe` que siempre lleva `title`, `loading="lazy"`
y una relación de aspecto estable:

```html
<figure class="demo">
  <iframe src="ejemplos/formulario.html" title="Formulario de inscripción"
          loading="lazy"></iframe>
  <figcaption>
    <span>Formulario accesible con validación nativa.</span>
    <a href="ejemplos/formulario.html">Abrir ejemplo</a>
  </figcaption>
</figure>
```

### Accesibilidad

Antes de dar una clase por terminada:

- Un solo `<h1>` por página y jerarquía de encabezados sin saltos.
- Todo control de formulario tiene `<label>` asociado.
- Las imágenes tienen `alt` descriptivo (o vacío si son decorativas).
- Los `iframe` tienen `title`.
- El foco es visible y la página se recorre completa con teclado.
- Los colores cumplen contraste AA (4.5:1 para texto normal).
- Las animaciones respetan `prefers-reduced-motion`.

### Validación

```bash
# Validar una página (requiere Java)
java -jar vnu.jar index.html

# O usar el validador en línea
# https://validator.w3.org/nu/
```

## Bibliografía

La bibliografía obligatoria y suplementaria está citada en la portada y en
cada clase. Los enlaces a eLibro requieren sesión institucional.
