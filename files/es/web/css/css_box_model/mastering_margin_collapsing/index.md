---
title: Entendiendo el colapso de margen
slug: Web/CSS/CSS_box_model/Mastering_margin_collapsing
---

Los márgenes [Top](/es/docs/Web/CSS/margin-top) y [bottom](/es/docs/Web/CSS/margin-bottom) de los bloques a veces están combinados (colapsados) en un solo margen cuyo tamaño es el mayor de los márgenes combinados, un comportamiento conocido como **colapso de margen**. Ten en cuenta que los márgenes de [flotantes](/es/docs/Web/CSS/float) y elementos con [posición absoluta](/es/docs/Web/CSS/position) nunca colapsan.

El colapso de margen ocurre en tres casos básicos:

- Hermanos adjacentes
  - : Los márgenes de los hermanos adjacentes son colapsados (excepto cuando el último hermano necesita ser [limpiado](/es/docs/Web/CSS/clear) después de usar los flotantes).
- Padre y primer/último hijo
  - : Si no hay un borde, padding, contenido en línea, [block formatting context](/es/docs/Web/CSS/CSS_display/Block_formatting_context) creado, o un _[limpiado](/es/docs/Web/CSS/clear)_ para separar el {{cssxref("margin-top")}} de un bloque del {{cssxref("margin-top")}} de su primer bloque hijo; o no hay borde, padding, contenido en línea, {{cssxref("height")}}, {{cssxref("min-height")}}, o {{cssxref("max-height")}} para separar el {{cssxref("margin-bottom")}} de un bloque del {{cssxref("margin-bottom")}} de su último hijo, entonces esos márgenes colapsan. El margen colapsado termina fuera del padre.
- Bloques vacíos
  - : Si no hay borde, padding, contenido en línea, {{cssxref("height")}}, o {{cssxref("min-height")}} para separar el {{cssxref("margin-top")}} de un bloque de su {{cssxref("margin-bottom")}}, entonces sus márgenes superiores e inferiores colapsan.

Cosas a tener en cuenta:

- Cuando estos casos están combinados ocurrirá un colapso de márgenes más complejo (de más de dos márgenes).
- Estas reglas se aplican incluso a márgenes con valor cero, así que el margen del primer/último hijo siempre termina fuera de su padre (de acuerdo a las reglas de arriba) independientemente de que el margen del padre sea o no sea cero.
- Cuando se trata de márgenes negativos, el tamaño del margen colapsado es la suma del margen positivo más grande y el margen negativo más pequeño (el más negativo).
- Cuando todos los márgenes son negativos, el tamaño del margen colapsado es el margen más pequeño (el más negativo). Esto se aplica tanto a los elementos adyacentes como a los elementos anidados.

## Ejemplos

### HTML

```html
<p>El margen inferior de este párrafo está colapsado ....</p>
<p>
  ... con el margen superior de este párrafo, lo que deja un margen de<code
    >1.2rem</code
  >
  entre ellos.
</p>

<div>
  Este elemento padre contiene dos párrafos!
  <p>
    Este párrafo tiene un margen de <code>.4rem</code> entre él y el texto
    anterior.
  </p>
  <p>
    Mi margen inferior se colapsa con mi padre, produciendo un margen inferior
    de <code>2rem</code>.
  </p>
</div>

<p>Estoy <code>2rem</code> por debajo del elemento de arriba.</p>
```

### CSS

```css
div {
  margin: 2rem 0;
  background: lavender;
}

p {
  margin: 0.4rem 0 1.2rem 0;
  background: yellow;
}
```

### Result

{{EmbedLiveSample('Ejemplos', 'auto', 350)}}

## También puedes ver

- [CSS Reference](/es/docs/Web/CSS/Reference)
- CSS Key Concepts: [CSS syntax](/es/docs/Web/CSS/CSS_syntax/Syntax), [at-rule](/es/docs/Web/CSS/CSS_syntax/At-rule), [comments](/es/docs/Web/CSS/CSS_syntax/Comments), [specificity](/es/docs/Web/CSS/CSS_cascade/Specificity) and [inheritance](/es/docs/Web/CSS/CSS_cascade/Inheritance), the [box](/es/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model), [layout modes](/es/docs/Glossary/Layout_mode) and [visual formatting models](/es/docs/Web/CSS/Visual_formatting_model), and [margin collapsing](/es/docs/Web/CSS/CSS_box_model/Mastering_margin_collapsing), or the [initial](/es/docs/Web/CSS/CSS_cascade/Value_processing), [computed](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing_e3410028f0a698ddd9f74225ea8d122c0a582707d683fdd173e681e62003518d), [resolved](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing_a47f4c6da6bce4fc52f8ed2ce27dc58e53fa5bd72bfef0bb04a61adbc5249cc4), [specified](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing_8a702f25e61d14d8bd6ee6f7e88ca236512427b92b01a92c1d11f9edbb8f5fe1), [used](/es/docs/Web/CSS/used_value), and [actual](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing) values. Definitions of [value syntax](/es/docs/Web/CSS/CSS_Values_and_Units/Value_definition_syntax), [shorthand properties](/es/docs/Web/CSS/CSS_cascade/Shorthand_properties) and [replaced elements](/es/docs/Web/CSS/CSS_images/Replaced_element_properties).
