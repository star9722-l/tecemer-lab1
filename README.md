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

## Flujo de datos (Semana 2)

Este proyecto consume la API pública **Open-Meteo** para obtener el pronóstico del clima de Huancayo (7 días).

### Fuente
- **API:** Open-Meteo (https://api.open-meteo.com/v1/forecast)
- **Datos:** Temperatura máxima, temperatura mínima y precipitación diaria.

### Transformación
1. Se consume la API con `requests` y se guarda la respuesta cruda en `pronostico_huancayo.json`.
2. Se convierte el JSON a CSV con el módulo `csv` → `pronostico_huancayo.csv`.
3. Se carga el CSV con Pandas, se agregan columnas derivadas (amplitud térmica, día lluvioso, categoría) y se generan resúmenes por categoría.

### Salida
- `pronostico_huancayo.json` → Datos crudos de la API.
- `pronostico_huancayo.csv` → Datos tabulados.
- `pronostico_huancayo_procesado.csv` → Datos con columnas derivadas.
- `resumen_por_categoria.csv` → Resumen agrupado por categoría de temperatura.

### Archivos del pipeline
- `numpy_demo.py` → Fundamentos de NumPy.
- `clima.py` → Consumo de API y conversión a CSV.
- `analisis.py` → Análisis con Pandas.