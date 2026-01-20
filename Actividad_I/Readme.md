# 📊 Predicción de Churn de Clientes mediante Regresión Logística

Esta actividad aplica técnicas de **Machine Learning** para identificar la probabilidad de abandono (churn) de clientes en una empresa de telecomunicaciones. Se exploran modelos de regresión logística con expansiones polinomiales y técnicas de regularización para optimizar la precisión y la interpretabilidad.

## 🚀 Estructura del Proyecto

El análisis se divide en 5 pasos críticos:
1. **Exploración y Preprocesamiento**: Limpieza de datos, imputación de valores faltantes (`TotalCharges`) y escalamiento robusto.
2. **Modelo Base**: Implementación de una regresión logística estándar con validación cruzada estratificada (K-Fold).
3. **Ingeniería de Características**: Generación de términos polinomiales de grado 2 e interacciones entre variables numéricas clave.
4. **Regularización**: Comparación de penalizaciones **Lasso (L1)** y **Ridge (L2)** para controlar el sobreajuste y realizar selección de variables.
5. **Análisis Crítico**: Evaluación de trade-offs entre Precision y Recall orientados al negocio.

## 🛠️ Tecnologías Utilizadas
* **Python 3.x**
* **Pandas & Numpy**: Manipulación de datos.
* **Scikit-Learn**: Modelado, validación cruzada y métricas.
* **Matplotlib & Seaborn**: Visualización estadística.

## 📈 Conclusiones
* **Efecto Lasso**: El modelo Lasso logró simplificar la complejidad polinomial, eliminando variables redundantes y manteniendo un alto F1-Score.
* **Métrica Primaria**: Se priorizó el **F1-Score** y **PR-AUC** debido al desbalance de clases (26% churn).
* **Hallazgo**: La interacción entre el cargo mensual y el tiempo de contrato resultó ser el predictor más fuerte de fuga.

## 👥 Autores
* Marcelo Carmona - Paula Alvarez
* Asignatura Machine Learning II
