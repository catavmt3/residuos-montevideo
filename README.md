# Recolección de Residuos en Montevideo
### Predicción y detección de anomalías

Especialización en Ciencia de Datos e Inteligencia Artificial · UTEC – MIT · 2025–2026  
**Equipo:** Catalina Vaz Martins · Emiliano Braña · Hugo Martinez

---

## Descripción

Pipeline de modelado sobre los registros de levantes de contenedores domiciliarios de la Intendencia de Montevideo (enero 2024 a febrero 2026). El objetivo es predecir los días de acumulación de residuos por contenedor y detectar anomalías (unidades que acumulan significativamente más de lo habitual) para optimizar la frecuencia de recolección.

## Contenido

El notebook `residuos_montevideo.ipynb` está organizado en las siguientes secciones:

1. **Carga y limpieza** — datos estáticos (contenedores y circuitos) y temporales (~8,9M registros)
2. **EDA y visualización geoespacial** — mapa de circuitos, distribución de días de acumulación
3. **Feature engineering** — variables temporales, clasificación de contenedores por comportamiento
4. **Pipeline de modelado** — construcción de secuencias temporales (ventana de 7 días)
5. **Baseline** — regresión lineal (MAE: 1.09 días · R²: 0.29)
6. **Modelo GRU** — arquitectura recurrente liviana (MAE: 0.83 días)
7. **Modelo LSTM** — con embedding de contenedor (RMSE: 1.37 · R²: 0.34)
8. **Análisis de residuales** — diagnóstico, sesgo y heterocedasticidad
9. **Sistema de detección de anomalías** — ruptura de patrón individual por contenedor

## Resultados destacados

- **~8,9 millones de registros** · **13.299 contenedores únicos**
- El LSTM con embedding logró el mejor RMSE (1.37 días) y R² (0.34)
- Sistema de anomalías con k=2.5σ: **recall 71%** — triplicando el enfoque de umbral fijo
- El canal con mayor potencial de mejora: reducir falsos negativos en contenedores de alta acumulación

## Stack

```
Python · PyTorch · LSTM · GRU · Scikit-learn · GeoPandas · Pandas · Matplotlib · Seaborn · Kaggle API
```

## Fuente de datos

Portal de datos abiertos de la Intendencia de Montevideo — [ckan.montevideo.gub.uy](https://ckan.montevideo.gub.uy/)  
Dataset disponible en Kaggle: `catalinavazmartins/residuosim`
