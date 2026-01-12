# Predicción de Abandono de Clientes (Customer Churn)
Este proyecto de Ciencia de Datos tiene como objetivo desarrollar un modelo de aprendizaje automático para predecir si un cliente abandonará una compañía de telecomunicaciones. Se enfoca en maximizar la detección de clientes con alta probabilidad de abandono.

## Descripción del Proyecto
El abandono de clientes es un problema crítico donde el coste de retener a un cliente existente es significativamente menor que el de adquirir uno nuevo. Este proyecto contiene:
- Análisis y Modelado: EDA , feature engineering y entrenamiento y selección de modelos (XGBoost, Random Forest, KNN).
- Optimización del modelo: El modelo final se optimiza no solo por accuracy (precisión), sino priorizando el Recall (sensibilidad) a través del F2-Score.
- Despliegue MLOps: Se empaquetó la aplicación con docker y se desplegó en Render.

## Tecnologías Utilizadas
- Python 3
- Manipulación de datos: Pandas, NumPy
- Machine Learning: Scikit-learn, XGBoost.
- Visualización: Matplotlib, Seaborn.
- Interpretabilidad: SHAP.
- Despliegue: Streamlit, Docker, Render

## Metodología del modelado

1. Preprocesamiento 
    - Imputación de valores faltantes.
    - Feature Scaling: Normalización con MinMaxScaler.
    - Encoding: One-Hot Encoding y mapeo binario.

2. Resultados del entrenamiento
El modelo XGBoost fue seleccionado por su capacidad de generalizar y rendimiento superior.

| Modelo |	ROC AUC |	
|--------|----------|
|XGBoost|	0.8428 |	
|Random Forest |	0.8420 |	
|KNN|	0.8136|	

3. Optimización del umbral de decisión del modelo
Se ajustó el umbral de decisión para maximizar el F2-Score (priorizando el rcall sobre la precision), dado que un falso negativo es más caro que un falso positivo.
- Umbral óptimo: 0.3915
- Recall alcanzado: 87.63%

## Explicabilidad del modelo
Se usaron los valores shap para la explicabilidad del modelo. Los factores clave identificados son:
- Aumento de probabilidad de abandono: Fibra Óptica, Cargos Mensuales altos y Pago por Cheque Electrónico.
- Disminución de probabilidad de abandono: Contratos de dos años y antigüedad (tenure).

## Despliegue
Se ha utilizado Streamlit para desarrollar la aplicación y docker para empaquetarla.  
El contenedor encapsula tanto el preprocesamiento de datos, como el modelo (XGBoost) y la lógica de la explicabilidad (SHAP).

### Hosting en Render
La aplicación está desplegada en Render en el siguiente enlace (puede tardar en iniciar): https://telecom-churn-app-deployment.onrender.com/  
El repositorio de github del deploy es: https://github.com/Ivan-0612/telecom-churn-app-deployment

