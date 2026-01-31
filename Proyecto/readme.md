# Detección Temprana de Obstrucciones en Pipelines mediante Machine Learning

![Python](https://img.shields.io/badge/python-3.12-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/sklearn-latest-orange.svg)
![XGBoost](https://img.shields.io/badge/xgboost-latest-green.svg)

## 📝 Descripción del Proyecto
Este proyecto desarrolla un sistema de detección temprana de obstrucciones en tuberías de larga distancia (143 km). Utiliza el **Método de las Características (MOC)** para simular la hidráulica transitoria y algoritmos de **Machine Learning** para clasificar estados operativos normales frente a obstrucciones.

**Autores:** Marcelo Carmona - Paula Alvarez

---

## 🚀 Metodología

### 1. Simulación y Generación de Datos (MOC)
Dado que las fallas reales son escasas, se construyó un motor de simulación basado en el MOC para resolver las ecuaciones hiperbólicas de flujo.
- **Calibración:** Parámetros óptimos hallados: Celeridad ($a$) y Fricción ($f$).
- **DataSet:** 20 simulaciones de 600s cada una, generando un dataset con sensores en los kilómetros 0, 30, 90, 92.5, 111, 135, 137.5 y 143.



### 2. Entrenamiento de Modelos Base
Se evaluaron cuatro algoritmos en sus configuraciones por defecto para establecer una línea base:

| Modelo | Accuracy | Precision | Recall | F1-score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 0.6386 | 0.6771 | 0.5300 | 0.5946 | 0.6443 |
| **SVM** | 0.5122 | 0.5184 | 0.3444 | 0.4139 | 0.5341 |
| **Random Forest** | **0.9208** | **0.9916** | **0.8489** | **0.9147** | **0.9907** |
| **XGBoost** | 0.7717 | 0.7971 | 0.7289 | 0.7615 | 0.8720 |

---

## 🛠️ Optimización de Hiperparámetros
Se aplicó `RandomizedSearchCV` con validación cruzada (`StratifiedKFold`) para maximizar el F1-Score en los modelos.

### Mejores Parámetros Hallados:

* **Random Forest (Modelo Ganador):**
    * `n_estimators`: 500
    * `max_features`: 'log2'
    * `min_samples_split`: 2
    * `max_depth`: None
    * **Mejor F1-Score: 0.9264**

* **XGBoost:**
    * `learning_rate`: 0.2, `n_estimators`: 300, `max_depth`: 5
    * **Mejor F1-Score: 0.7828**

* **SVM:**
    * `kernel`: 'rbf', `C`: 100, `gamma`: 'auto'
    * **Mejor F1-Score: 0.8400**

---

## 📈 Resultados Finales y Estabilidad
El modelo **Random Forest** fue seleccionado por su robustez ante el ruido y su excelente desempeño en el recall de obstrucciones.

### Matriz de Confusión e Importancia de Sensores
El análisis de importancia de características reveló que los sensores en el **Km 0** y el bloque de sensores entre el **Km 90 y 111** son determinantes para identificar el rebote de la onda de presión causado por la obstrucción.



### Validación Cruzada (5-Fold Estratificado)
Los resultados finales de estabilidad para el modelo RF optimizado:
- **Accuracy promedio:** 99.0% (± 0.00)
- **Precision promedio:** 99.0% (± 0.00)
- **F1-score promedio:** 99.0% (± 0.00)

---

## 📂 Estructura del Repositorio
- `Data.xlsx`: Datos para calibración física.
- `notebook.ipynb`: Código completo (EDA, MOC, ML).
- `dataset_entrenamiento_obstrucciones.csv`: Datos sintéticos generados.

---
