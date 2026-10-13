# NightBuilds-lakehouse-spark

> Lakehouse en tres capas con PySpark sobre millones de viajes de taxi, con la optimización medida en la Spark UI.

**Estado:** 🚧 sin empezar · **Categoría:** NightBuilds · **Tipo:** ETL distribuido · **Módulo del programa:** 06 · Spark

## Qué significa el nombre

El prefijo del repositorio indica el tamaño del proyecto:

| Prefijo | Tamaño | Qué es |
|---|---|---|
| `DevSandbox-` | Hasta 8 h | Un proyecto pequeño para practicar un tema concreto: un espacio para probar, equivocarse y terminar rápido |
| **`NightBuilds-`** ← este | 8 h o más | Un proyecto grande, con varias piezas (base de datos, orquestación, nube o API) y decisiones de diseño propias |

Este es un **NightBuilds**: el reto está estimado en 10–12 h.

## La problemática

Una empresa de movilidad quiere saber cuándo y dónde tiene más demanda, pero sus datos son millones de viajes: demasiados para pandas. Hay que procesarlos en capas (bronze, silver, gold) y demostrar con mediciones que el job está optimizado.

## Los datos

| Dónde | Qué es |
|---|---|
| <https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page> | Página oficial de NYC TLC: todos los meses y el diccionario de datos |
| <https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2025-01.parquet> | Un mes de ejemplo en Parquet (enero de 2025, unos 59 MB). No lo subas al repositorio |

## Qué hay que construir

El enunciado completo, con sus hitos y cómo comprobar cada uno, está en [`RETO.md`](RETO.md). No trae solución: el diseño es tuyo.

- [`docs/REGLAS.md`](docs/REGLAS.md): cómo se trabaja un NightBuild y qué debe tener este README al terminar.
- [`docs/RUBRICA.md`](docs/RUBRICA.md): con qué criterios se evalúa.

## Cómo se ejecuta

*Pendiente: se escribe al cerrar el primer hito. Los comandos exactos, desde `git clone`.*

## Decisiones

*Pendiente: tres decisiones técnicas y la alternativa que se descartó en cada una.*

## Qué aprendí

*Pendiente.*

---

Reto del programa de Python e ingeniería de datos: [UNIR_Python_Certification](https://github.com/KevinMondragonDev/UNIR_Python_Certification).
