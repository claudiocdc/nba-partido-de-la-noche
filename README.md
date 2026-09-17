# KPI del Partido de la Noche — NBA

Cada noche se juegan varios partidos de la NBA. ¿Cuál merece la pena ver?
Este proyecto calcula un **KPI de 0 a 100** para cada partido de una fecha y los
ordena, para responder a esa pregunta con datos en lugar de intuición.

## ¿Cómo funciona el KPI?

El KPI combina cuatro factores. Cada uno se normaliza a una escala de 0 a 1 y se
pondera según su importancia:

| Factor      | Qué mide                                              | Peso |
|-------------|------------------------------------------------------|------|
| Igualdad    | Lo apretado del marcador final                       | 45 % |
| Estrella    | La mejor actuación individual (Game Score de Hollinger) | 30 % |
| Prórrogas   | Si el partido se fue a la prórroga                   | 20 % |
| Ritmo       | Los puntos totales anotados                          | 5 %  |

Los pesos son una **hipótesis de partida**: reflejan mi criterio sobre qué hace
interesante un partido (prioriza la igualdad y las grandes actuaciones). Se pueden
recalibrar mirando datos reales, y están centralizados en un único lugar del código
para facilitarlo.

## Fuente de datos

- **[nba_api](https://github.com/swar/nba_api)** — cliente de la API oficial de
  estadísticas de la NBA (stats.nba.com). Datos oficiales de la liga.
- La actuación individual se mide con el **Game Score de Hollinger**, una métrica
  estándar de baloncesto que resume el rendimiento de un jugador en un solo número
  a partir del box score tradicional.

## Uso

1. Instala las dependencias: `pip install nba_api pandas`
2. En el notebook, indica la fecha a analizar.
3. Ejecuta todas las celdas.
4. Obtienes el ranking de los partidos de esa noche, con el "partido de la noche"
   coronado y el desglose de cada métrica.

> **Nota:** la API de la NBA solo responde a IPs residenciales, así que el notebook
> debe ejecutarse en un ordenador local (no funciona desde la nube, como Colab).

## Tecnologías

Python · pandas · nba_api · Jupyter Notebook

## Notas de diseño

- Es una **v1**: los umbrales (qué margen es "paliza", qué Game Score es "de época")
  y los pesos son decisiones calibrables, no verdades absolutas.
- El código separa el **motor** (funciones de puntuación + pesos) de la recolección
  de datos, para poder recalibrar el criterio sin tocar la lógica.

## Próximos pasos

- Automatizar la ejecución diaria y recibir el ranking por email.
- Procesar la temporada completa para encontrar el partido más emocionante del año.

---

Proyecto personal de análisis de datos.
