# InfoArg: fichas automáticas para artículos de Wikipedia sobre Argentina

Trabajo Práctico Integrador de Procesamiento de Lenguaje Natural, Universidad de Palermo.
Integrantes: Mirko Doljanica Monge y Rashid Zuain.

InfoArg toma el texto de un artículo de Wikipedia y hace dos cosas:

1. **Clasifica el tipo de entidad:** persona, lugar, organización, evento, obra o cosa.
2. **Extrae los datos clave** y arma un borrador de infobox.

## Resultados principales

| Tarea | Resultado |
|---|---|
| Clasificación (test, 200 artículos) | F1 macro ≈ 0,81 con TF-IDF o embeddings; Transformer desde cero 0,71 ± 0,02 (5 semillas) |
| Año de nacimiento | 94% de acierto |
| Lugar de nacimiento | 80% de acierto |
| Año de fallecimiento | 90% de acierto |
| Año de fundación (organizaciones) | 62% de acierto |
| Artículos sin infobox | 208 borradores en `borradores_infobox.csv` (84 marcados para revisar) |

## Cómo correrlo

```bash
pip install -r requirements.txt
python -m spacy download es_core_news_lg
jupyter notebook TP_InfoArg.ipynb
```

El notebook descarga el corpus `corpus-wiki-arg.jsonl` (repositorio de la cátedra) en `data/` y guarda las
tablas en `resultados/` y los gráficos en `figuras/`. Corre en CPU en unos 6–7 minutos; lo que más tarda es el
Transformer, que se entrena con 5 semillas. En Colab, antes de ejecutarlo hay que correr
`!python -m spacy download es_core_news_lg`.

## Estructura

| Archivo | Contenido |
|---|---|
| `TP_InfoArg.ipynb` | Notebook completo y ejecutado: EDA, clasificación, extracción y pipeline |
| `clasificacion.csv`, `extraccion_personas.csv` | Tablas de métricas |
| `borradores_infobox.csv` | Borradores de infobox para los artículos sin ficha |
| `eda.png`, `clasificacion.png` | Gráficos usados en el informe |
