# 🚀 NightBuild — Lakehouse con Spark

**Repositorio:** `NightBuilds-lakehouse-spark` · **Tipo:** ETL distribuido · **Tiempo:** 10–12 h · **Después de:** `02_retos_por_tema` y las fases 1 a 10 de `01_ruta_sparksql`

> Reglas, README y lista de cierre: [`NIGHTBUILDS.md`](docs/REGLAS.md). **No hay solución: el diseño es tuyo.**

## El caso

Una empresa de movilidad quiere saber cuándo y dónde tiene más demanda. Los datos son millones de viajes: demasiados para pandas en un portátil con poca memoria. Los procesas con PySpark en tres capas (bronze, silver, gold) y demuestras que tu job está **optimizado**, no solo que funciona.

Datos: un dataset público grande de tu elección. Los registros de viajes de taxi de Nueva York (NYC TLC Trip Record Data, en Parquet) son el clásico; descarga 3 meses desde <https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page>. Cada mes tiene esta forma: <https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2025-01.parquet> (unos 59 MB).

## Qué practicas

| Fase | Dónde aparece |
|---|---|
| 04–05 DataFrames | Limpieza, joins y window functions |
| 06–07 Spark SQL | Los agregados de la capa gold |
| 08 Optimización | Particiones, shuffle, broadcast, caché: medido en la Spark UI |
| 09 Proyecto integrador | La estructura modular del pipeline |
| 10 Despliegue | `spark-submit` en tu clúster local |

## Hitos

**Hito 1 — Bronze.** Lee los archivos tal como vienen, con esquema explícito, y escríbelos particionados por fecha de ingesta.
*Comprueba:* cuenta las filas y anótalas: es tu cifra de control.

**Hito 2 — Silver.** Tipos correctos, sin duplicados, sin viajes imposibles (duración o distancia negativa, fechas fuera de rango). Lo rechazado se cuenta por motivo.
*Comprueba:* bronze = silver + rechazados.

**Hito 3 — Gold.** Tres tablas: demanda por hora y zona, ingreso diario con media móvil de 7 días, y ranking de zonas por mes (window function).
*Comprueba:* un total de gold coincide con el mismo cálculo hecho sobre silver.

**Hito 4 — Optimizar con evidencia.** Elige el job más lento. Mide antes, cambia **una** cosa (particiones, broadcast, caché, filtro antes del join), mide después. Repite tres veces.
*Comprueba:* una tabla en el README con tiempo, nº de shuffles y captura de la Spark UI antes y después.

**Hito 5 — Como un job de verdad.** Un punto de entrada con parámetros (`--mes`, `--entrada`, `--salida`) lanzado con `spark-submit` en tu clúster standalone. Relanzar un mes lo sobrescribe sin duplicar.
*Comprueba:* dos ejecuciones del mismo mes dejan las mismas filas.

## Preguntas para defenderlo

- ¿Qué operación provocaba el shuffle más caro y cómo lo redujiste?
- ¿Por qué elegiste esa columna de partición al escribir? ¿Cuántos archivos genera?
- ¿Dónde habría *skew* en estos datos y cómo lo detectarías?
- ¿Qué cambia en tu código para correrlo en EMR Serverless?

## Súbelo de nivel

- Tests de las transformaciones con pytest y DataFrames pequeños.
- Capas en S3 sobre **Floci** (conector `s3a`), con el endpoint en la configuración.
- Delta Lake o Iceberg en la capa silver.
