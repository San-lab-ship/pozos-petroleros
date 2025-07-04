# Predicción de Producción de Petróleo en Pozos Colombianos 

El objetivo de este proyecto es la Predicción de Producción de Petróleo en Pozos Colombianos, a través del desarrollo de un modelo de machine learning capaz de anticipar la producción diaria (BPD) en pozos ubicados en diversas cuencas sedimentarias. Este análisis se centrará en departamentos clave como Meta, Casanare, Santander, Arauca y Putumayo. El modelo permitirá no solo proyectar la eficiencia productiva de los pozos, sino también evaluar el impacto de intervenciones operativas específicas, tales como el fracturamiento hidráulico, los cambios de bomba o la estimulación ácida.

## Descripción del Problema
Conocer de antemano la producción de crudo de un pozo es clave para planear mantenimientos, programar operaciones y optimizar recursos. Este proyecto utiliza un conjunto de datos simulados de producción diaria y eventos de intervención para construir un modelo predictivo robusto, aprovechando técnicas modernas de aprendizaje automático.

## Arquitectura 

Aquí se presenta la arquitectura de alto nivel del sistema de predicción de producción de petróleo:

![Arquitectura de pozos petroleros en Colombia](arquitectura_pozos_petroleros.png)

## Metodología
1. Carga y Exploración Inicial de Datos
✔️ DataFrames: df_produccion y df_intervenciones
✔️ Identificación de columnas clave, tipos de datos y fechas

2. Limpieza y Preparación
✔️ Fechas convertidas a datetime
✔️ Dataset unificado: df_merged

3. Feature Engineering
✔️ Variables temporales (lags, medias móviles)
✔️ Indicadores de intervención (como en_intervencion_activa)
✔️ Más de 50 variables predictoras generadas

4. Preprocesamiento de Datos
✔️ Variables numéricas: StandardScaler
✔️ Variables categóricas: OneHotEncoder
✔️ Transformación mediante ColumnTransformer
✔️ Obtención de X_train_processed y X_test_processed

5. Entrenamiento y Optimización del Modelo
Se entrenó un RandomForestRegressor optimizado con RandomizedSearchCV y validación cruzada 3-fold.

## Parámetros Óptimos del RandomForestRegressor:

| Parámetro         | Valor Óptimo |
|-------------------|--------------|
| `n_estimators`    | 72           |
| `max_features`    | 0.85         |
| `min_samples_leaf`| 17           |
| `max_depth`       | 15           |

6. Evaluación del Modelo Final
Métricas de Desempeño:

| Métrica | Valor     |
|---------|-----------|
| `R²`    | 0.9575    |
| `MAE`   | 45.23 BPD |
| `RMSE`  | 67.89 BPD |

## Análisis de Errores
Se identificaron los 10 errores más altos (positivos y negativos) para detectar sobreestimaciones y subestimaciones. Este análisis ayudó a validar la robustez del modelo frente a distintos escenarios de producción.

## Visualizaciones del Análisis
1. Producción de Petróleo para el POZO_001 con Intervenciones
![image](https://github.com/user-attachments/assets/05e51d2a-fe75-404a-a734-277abcf62803)

2. Costo Promedio por Tipo de Intervención (USD)
![image](https://github.com/user-attachments/assets/5d0fd580-5ff8-4472-93da-22b918ecb558)

3. Mapa Interactivo con los 5 Departamentos Petroleros
https://san-lab-ship.github.io/pozos-petroleros/mi_mapa_interactivo%20(1).html

4. Producción Real vs. Predicha para POZO_001
https://san-lab-ship.github.io/pozos-petroleros/produccion_Pozo.html

5. Análisis de Producción y Seguridad en Pozos Petroleros por Departamento
![image](https://github.com/user-attachments/assets/7738c2ae-5142-42c0-8034-868fc1135fe3)


## Tecnologías Utilizadas

✔️Python 3.10
✔️Pandas
✔️NumPy
✔️Scikit-learn
✔️Plotly
✔️Folium
✔️Jupyter Notebook / Google Colab
✔️Joblib
✔️Draw.io

## Conclusión

El modelo final basado en Random Forest demostró una alta capacidad predictiva (R² de 0.9575) y una baja desviación de error, incluso en datos no vistos. La combinación de un pipeline robusto de procesamiento, ingeniería de características (incluyendo el impacto de las intervenciones) y herramientas de visualización hace que este modelo sea apto para aplicaciones reales en operaciones de campo o sistemas de monitoreo de producción petrolera.


## Estructura del Proyecto

```
pozos-petroleros/
├── README.md
├── arquitectura
├── notebooks/
├── src/
│   ├── data_generation.py
│   ├── model_training.py
│   ├── visualizations.py
│   └── main.py
├── models/
├── results/
│   ├── mapa_pozos_interactivo.html
│   └── produccion_POZO_001.html
├── docs/
│   └── produccion_pozo_001.png
├── requirements.txt
└── .gitignore```
