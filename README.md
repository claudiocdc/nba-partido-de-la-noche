# NBA - El Partido de la Noche

**Un KPI (0-100) que puntúa cómo de entretenido es cada partido de la NBA, para responder a una pregunta simple: ¿qué partido veo esta noche?**

## El problema

Cada noche hay entre 5 y 10 partidos de la NBA y no da tiempo a verlos todos. ¿Cuál merece la pena? En lugar de fiarme del instinto, construí una métrica que puntúa de forma objetiva lo entretenido que es un partido.

## El KPI

El KPI combina cuatro ingredientes, cada uno normalizado (0-1) y con su peso:

| Componente | Qué mide | Peso |
|---|---|---|
| **Igualdad** | Lo ajustado del marcador final | 45% |
| **Estrella** | La mejor actuación individual (Game Score) | 30% |
| **Prórrogas** | Si hubo tiempo extra (y cuántos) | 20% |
| **Ritmo** | Puntos totales del partido | 5% |

## Estructura del proyecto

| Notebook | Qué hace |
|---|---|
| `00_recoleccion_datos.ipynb` | Descarga toda la temporada 2025-26 vía `nba_api` y calcula el KPI de cada partido → `kpi_temporada.csv` |
| `01_kpi_diario.ipynb` | El motor del KPI para el día a día: le das una fecha, te dice qué partido ver |
| `02_analisis_temporada.ipynb` | Valida el KPI sobre la temporada completa (1.329 partidos) |

## Hallazgos clave

Al validar el KPI contra una temporada real, los resultados coinciden con la realidad:

-  **El mejor partido** fue el DEN vs MIN de Navidad (KPI 85.0), que la prensa bautizó como el *"Christmas Miracle"* de Denver.
-  **El equipo más divertido** fue Denver, con diferencia sobre el resto.
-  **El "MVP del entretenimiento"** fue Shai Gilgeous-Alexander — y el top 4 reprodujo el podio real del MVP de la temporada.
-  Solo un **7.45%** de los partidos son verdaderos "partidazos" (KPI > 60).
-  **La liga se calienta en playoffs:** el KPI medio se dispara en las rondas finales.

## Tecnologías

`Python` · `pandas` · `nba_api` · `seaborn` · `matplotlib` · `Jupyter`

## Cómo ejecutarlo

El dataset ya procesado (`kpi_temporada.csv`) viene incluido, así que puedes ejecutar directamente el análisis (`02`) sin necesidad de descargar nada.

> **Nota:** `nba_api` solo funciona desde una IP residencial (no en la nube ni en Colab), y descargar la temporada entera tarda un rato. Por eso incluyo el CSV ya generado, para que el proyecto sea reproducible al instante.
