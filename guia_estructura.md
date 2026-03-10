# Estructura del Diccionario Cuervo (JSON)

Para facilitar la comprensión y futura expansión del proyecto, aquí se detalla la jerarquía y los campos extraídos del diccionario original:

## Jerarquía de Datos

El diccionario se organiza de forma jerárquica para preservar la lógica lexicográfica original:

1.  **Lema (Palabra Principal)**: El término que se define (ej. "ABANDONAR").
2.  **Categoría Gramatical**: Indica si es verbo, sustantivo, etc.
3.  **Introducción**: Texto introductorio con definiciones generales o breves sinónimos.
4.  **Acepciones (Grupos Principales)**: Marcadas con letras latinas minúsculas (**a, b, c...**).
    - **Definición**: El significado específico de esa acepción.
    - **Ejemplos/Citas**: Fragmentos literarios o frases de ejemplo que ilustran el uso.
5.  **Sub-acepciones / Construcciones**: Marcadas con letras griegas (**α, β, γ...** o **α α, β β...**).
    - Cuelgan de una acepción principal.
    - Contienen su propia definición y su propio set de ejemplos.
6.  **Construcciones Sintácticas (Sección Final)**: Presente en lemas complejos, contiene una lista de preposiciones y casos de uso con enlaces a las acepciones correspondientes.
7.  **Etimología**: Origen de la palabra, generalmente al final del artículo.

## Campos del Objeto JSON

```json
{
  "lema": "String (con HTML)",
  "categoria_gramatical": "String",
  "introduccion": "String (HTML)",
  "acepciones": [
    {
      "id": "a), b)...",
      "definicion": "String (HTML)",
      "ejemplos_citas": [
        {
          "texto_cita": "String (HTML)",
          "autor": "String (HTML)",
          "referencia_obra": "String (HTML)"
        }
      ],
      "subacepciones": [
        {
          "id_marcador_html": "String (HTML)",
          "id_limpio": "— α )",
          "definicion": "...",
          "ejemplos_citas": [...]
        }
      ]
    }
  ],
  "construccion_sintactica": "String (HTML con enlaces)",
  "etimologia": "String (HTML)"
}
```

## Notas Técnicas

- **HTML**: Se han preservado las etiquetas de formato (`<i>`, `<b>`, `<font>`) dentro de las cadenas de texto para mantener la estética original del diccionario en el visor.
- **Símbolos**: Los caracteres especiales de la fuente original se han mapeado a sus equivalentes Unicode estándar (ej. `¾` -> `—`).
