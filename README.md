# tecemer-lab1

Proyecto básico para el curso de Tecnologías Emergentes.

## Instalación

1. Crea el entorno virtual: `python -m venv .venv`
2. Activa el entorno: `.venv\Scripts\activate`
3. Instala el proyecto: `pip install -e .`

## Uso

Ejecuta el script con:
`python src/tecemer_lab1/app.py`

## Estructura

- `src/`: Contiene el código del proyecto.
- `pyproject.toml`: Configuración del proyecto.
- `.gitignore`: Archivos que no se suben a GitHub.

## Autor

Palacios Meza Briyid Estrella - Tecnologías Emergentes - ISO46B

## Flujo de datos — Semana 2

Esta sección documenta el pipeline de datos construido en la Semana 2 (Librerías para Datos y Automatización).

*Fuente:* API pública Open-Meteo (https://api.open-meteo.com/v1/forecast), sin necesidad de clave de acceso. Se consulta el pronóstico de 7 días para Huancayo (latitud -12.07, longitud -75.21): temperatura máxima, temperatura mínima y precipitación diaria.

*Transformación:*
1. clima.py consume la API con requests (timeout de 5s y manejo de excepciones) y guarda la respuesta cruda en pronostico_huancayo.json.
2. La misma respuesta se convierte a pronostico_huancayo.csv con el módulo estándar csv.
3. analisis.py carga el CSV en un DataFrame de Pandas, agrega las columnas derivadas amplitud_termica, dia_lluvioso y categoria (frío/templado/cálido), y calcula un resumen agrupado por categoría con groupby.

*Salida:*
- pronostico_huancayo.json — respuesta cruda de la API (trazabilidad del dato original).
- pronostico_huancayo.csv — datos tabulares sin procesar.
- pronostico_huancayo_procesado.csv — datos con las columnas derivadas.
- resumen_por_categoria.csv — agregación por categoría de temperatura.

*Cómo reproducirlo:*
bash
python clima.py
python analisis.py