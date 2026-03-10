# Diccionario de Construcción y Régimen (DCR) - Cuervo

Este repositorio contiene la versión digital y refinada del **Diccionario de Construcción y Régimen de la Lengua Castellana** de Rufino José Cuervo. Los datos han sido extraídos del **Diccionario de construcción y régimen de la lengua castellana en CD-ROM** (1ª ed.). Barcelona: Herder Editorial, y han sido transformados a un formato **JSON estructurado** para su visualización a través de una aplicación web ligera.

## 🚀 Vista Rápida

- **URL del Visor**: [https://johnatanebonilla.github.io/dcr/](https://johnatanebonilla.github.io/dcr/)
- **Lemas procesados**: 2758
- **Tecnologías**: Python (Conversión), JavaScript/HTML/CSS (Visor).

## 🛠️ Proceso de Conversión (`mass_convert.py`)

El script de Python realiza las siguientes tareas críticas para garantizar la integridad de los datos:

1.  **Traducción de Símbolos Griegos**: Convierte caracteres de la fuente _Symbol_ (propios de Windows antiguo) a Unicode estándar. Protege las etiquetas HTML para evitar romper enlaces.
2.  **Detección de Sub-acepciones**: Utiliza expresiones regulares avanzadas para identificar marcadores griegos (`— α )`, `α α )`, etc.) que a menudo están fragmentados en el HTML original.
3.  **Balanceo de Etiquetas**: Cierra automáticamente etiquetas de formato (`<i>`, `<b>`, `<font>`) que quedaron abiertas en los bloques originales, evitando que el estilo se derrame en el resto de la interfaz.
4.  **Extracción de Sintaxis**: Captura la sección de "Construcción" (`Constr.`) presente en lemas complejos, manteniendo los hipervínculos internos.
5.  **Generación de Índice**: Crea un archivo `index_db.json` con todos los lemas para permitir la búsqueda instantánea en el visor.

## 📂 Estructura del Repositorio

- `index.html`: Punto de entrada del visor web.
- `app.js` / `style.css`: Lógica y diseño de la interfaz.
- `json/`: Carpeta con los 2700+ archivos JSON (uno por lema).
- `mass_convert.py`: Script documentado utilizado para la transformación de datos.
- `guia_estructura.md`: Detalle técnico de los campos del JSON.

## 📄 Estructura de un Lema (JSON)

Cada entrada sigue este esquema:

```json
{
  "lema": "Palabra",
  "categoria_gramatical": "...",
  "introduccion": "Definición general...",
  "acepciones": [
    {
      "id": "a)",
      "definicion": "...",
      "ejemplos_citas": [...],
      "subacepciones": [...]
    }
  ],
  "construccion_sintactica": "Sección técnica...",
  "etimologia": "..."
}
```

## 👩‍💻 Uso Local

Si deseas ejecutar el conversor o el visor localmente:

1. Asegúrate de tener los archivos `.htm` originales en una carpeta `/html`.
2. Ejecuta `python mass_convert.py`.
3. Para ver los resultados, inicia un servidor local: `python -m http.server 8000` y abre `localhost:8000`.

## Créditos y Citación

Este proyecto ha sido desarrollado por **Johnatan E. Bonilla** en el marco del proyecto **“Observatorio Ecosistema Digital de Lenguas de Colombia”**, vinculado a la **Línea de investigación en Lingüística de Corpus y Computacional** del **Grupo de Investigaciones** del **Instituto Caro y Cuervo**.

Si utilizas estos datos o esta herramienta en una investigación académica, por favor cita tanto el desarrollo técnico como las fuentes originales en formato APA:

### Desarrollo Técnico

- Bonilla, J. E. (2026). _Visor Digital del Diccionario de Construcción y Régimen de la Lengua Castellana_. [https://github.com/johnatanebonilla/dcr](https://github.com/johnatanebonilla/dcr)

### Fuentes Originales

- Cuervo, R. J. (1886). _Diccionario de construcción y régimen de la lengua castellana_. París: Roger.
- Cuervo, R. J. (2002). _Diccionario de construcción y régimen de la lengua castellana en CD-ROM_ (1ª ed.). Barcelona: Herder Editorial.
- Instituto Caro y Cuervo. (1954–1994). _Diccionario de construcción y régimen de la lengua castellana_ (Vols. 3–8). Bogotá: Instituto Caro y Cuervo.

---

_Proyecto de preservación y digitalización lexicográfica._
