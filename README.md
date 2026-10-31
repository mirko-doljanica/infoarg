# InfoArg: fichas automáticas para artículos de Wikipedia sobre Argentina

Trabajo Práctico Integrador de Procesamiento de Lenguaje Natural, Universidad de Palermo.
Integrantes: Mirko Doljanica Monge, Jimena Medina y Rashid Zuain.

InfoArg toma el texto de un artículo de Wikipedia y hace dos cosas:

1. **Clasifica el tipo de entidad:** persona, lugar, organización, evento, obra o cosa.
2. **Extrae los datos clave** y arma un borrador de infobox.

## Resultados principales

| Tarea | Resultado |
|---|---|
| Clasificación (test, 200 artículos) | F1 macro ≈ 0,81 con TF-IDF o embeddings; Transformer desde cero ≈ 0,69–0,74 |
| Año de nacimiento | 94% de acierto |
| Lugar de nacimiento | 80% de acierto |
| Año de fallecimiento | 90% de acierto |
| Año de fundación (organizaciones) | 62% de acierto |
| Artículos sin infobox | 208 borradores generados en `resultados/borradores_infobox.csv` |

## Cómo correrlo

```bash
pip install -r requirements.txt
python -m spacy download es_core_news_lg
jupyter notebook TP_InfoArg.ipynb
```

El notebook descarga el corpus `corpus-wiki-arg.jsonl` (repositorio de la cátedra) en `data/`. Corre en CPU en unos 5 minutos.

## Estructura

| Archivo | Contenido |
|---|---|
| `TP_InfoArg.ipynb` | Notebook completo y ejecutado: EDA, clasificación, extracción y pipeline |
| `clasificacion.csv`, `extraccion_personas.csv` | Tablas de métricas |
| `borradores_infobox.csv` | Borradores de infobox para los artículos sin ficha |
| `eda.png`, `clasificacion.png` | Gráficos usados en el informe |
