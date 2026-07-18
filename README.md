# Sprint_7

Análisis de Clientes — ConnectaTel

Análisis exploratorio del comportamiento de los clientes de **ConnectaTel**, una empresa de telecomunicaciones en Latinoamérica, con datos registrados hasta 2024. El objetivo es construir un perfil estadístico de los clientes, detectar comportamientos atípicos y crear segmentos que orienten estrategias de retención y mejora de planes.

## Datasets

- **`plans.csv`** — planes disponibles (precio mensual, minutos y GB incluidos, costos por extra). 2 planes: Básico y Premium.
- **`users_latam.csv`** — 4 000 clientes (edad, ciudad, fecha de registro, plan, fecha de baja).
- **`usage.csv`** — 40 000 eventos de uso real (llamadas y mensajes) durante 2024.

## Etapas del análisis

1. **Carga y exploración** — estructura, tipos de datos y vista preliminar de los tres datasets.
2. **Calidad de datos** — detección de nulos, *sentinels* (`age = -999`, `city = "?"`) y fechas fuera de rango (registros con año 2026).
3. **Limpieza** — imputación de edad con la mediana, conversión de sentinels a nulos, marcado de fechas imposibles y verificación de nulos MAR en `duration`/`length`.
4. **Summary statistics por usuario** — agregación del uso por cliente (mensajes, llamadas y minutos) y unión con la tabla de usuarios.
5. **Visualización y outliers** — histogramas por plan, boxplots y cálculo de límites con el método IQR.
6. **Segmentación** — grupos por nivel de uso (Bajo / Medio / Alto) y por edad (Joven / Adulto / Adulto Mayor).
7. **Insight ejecutivo** — hallazgos y recomendaciones accionables para el negocio.

## Principales hallazgos

- ~65% de los clientes usan el plan **Básico** y ~35% Premium.
- La base es mayoritariamente **adultos (30–59)** con **uso medio** (~74%).
- El valor se concentra en un pequeño segmento de **alto uso** (~7%), con minutos de llamada que llegan hasta ~156.
- Problemas de datos corregidos: sentinel de edad (55 filas), ciudad desconocida (~14%), y 40 fechas de registro imposibles.

## Cómo ejecutar

Requisitos: `python 3`, `pandas`, `numpy`, `seaborn`, `matplotlib`.

```bash
pip install pandas numpy seaborn matplotlib jupyter
jupyter notebook "S7 Version-Estudiante-Project-ConnectaTel.ipynb"
```

El notebook lee los CSV desde la misma carpeta (`plans.csv`, `users_latam.csv`, `usage.csv`). También puede abrirse en **Google Colab** subiendo el notebook y los tres archivos, o ajustando las rutas a `/datasets/` si se ejecuta en la plataforma de TripleTen. Ejecutar las celdas en orden (`Kernel → Restart & Run All`) reproduce todo el análisis.
