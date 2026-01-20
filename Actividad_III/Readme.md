# Actividad III – *Machine Learning II*
Autores: Marcelo Carmona - Paula Alvarez

## 📌 Descripción General
Este proyecto corresponde a la **Actividad 3 del curso Machine Learning II**.
El objetivo es aplicar distintos modelos de clasificación al problema de **churn prediction** (abandono de clientes), evaluando su desempeño y discutiendo ventajas, limitaciones e interpretabilidad.

Se implementan dos enfoques principales:
- **Naïve Bayes** (GaussianNB y BernoulliNB).
- **Support Vector Machines (SVM)** con kernel lineal y RBF.

Además, se incluyen diagnósticos de dependencia entre predictores (correlaciones, Cramér’s V, VIF) para analizar el impacto en los supuestos de los modelos.

---

## 🛠️ Librerías Utilizadas
- **Manipulación y visualización:** `numpy`, `pandas`, `matplotlib`, `seaborn`
- **Modelado:** `scikit-learn` (pipelines, preprocesamiento, Naïve Bayes, SVM, métricas)
- **Estadística:** `scipy.stats.contingency` (Cramér’s V)
- **Infraestructura:** `google.colab` para montaje de Google Drive

---

## 🔄 Flujo del Código
1. **Carga de datos:**  
   - Dataset `data-churn.csv` desde Google Drive.  
   - Exploración inicial: distribución de la variable objetivo, estadísticas básicas.

2. **Preprocesamiento:**  
   - Imputación de valores faltantes (mediana/moda).  
   - Escalado de numéricas con `StandardScaler`.  
   - Codificación categórica con `OneHotEncoder`.  
   - Conversión de variable objetivo a formato binario.

3. **Modelos Naïve Bayes:**  
   - **GaussianNB:** sobre matriz densa (numéricas escaladas + one-hot).  
   - **BernoulliNB:** discretización de numéricas en 2 bins + one-hot.  
   - **GridSearchCV** para optimización de hiperparámetros.  
   - Evaluación con métricas: Accuracy, F1 macro, ROC-AUC, PR-AUC.

4. **Diagnóstico de Dependencia:**  
   - Correlaciones Pearson/Spearman globales y por clase.  
   - Asociación categórica con **Cramér’s V**.  
   - Multicolinealidad numérica con **VIF**.  
   - Discusión sobre impacto en supuestos de independencia de Naïve Bayes.

5. **Modelos SVM:**  
   - **Lineal (LinearSVC)**: interpretabilidad vía pesos.  
   - **RBF (SVC kernel=rbf)**: captura no linealidad.  
   - **RandomizedSearchCV** para hiperparámetros `C` y `gamma`.  
   - Calibración de probabilidades con `CalibratedClassifierCV`.  
   - Evaluación en test con métricas y curvas ROC/PR.

6. **Análisis Crítico:**  
   - Comparación entre NB y SVM.  
   - Discusión sobre interpretabilidad, escalamiento, dimensionalidad y calibración de probabilidades.

---

## 📊 Resultados Obtenidos

### Naïve Bayes
- **GaussianNB** y **BernoulliNB** fueron entrenados.  
- Selección final basada en **F1 macro**.  
- Métricas en test (ejemplo representativo):
  - Accuracy ≈ 0.80  
  - F1 macro ≈ 0.78  
  - ROC-AUC macro ≈ 0.82  
  - PR-AUC macro ≈ 0.75  
- Se observó que la **dependencia entre predictores** afecta la calibración de probabilidades.

### SVM
- **Lineal (calibrado):**
  - Accuracy ≈ 0.82  
  - F1 macro ≈ 0.80  
  - ROC-AUC macro ≈ 0.84  
  - PR-AUC macro ≈ 0.77  
- **RBF (calibrado):**
  - Accuracy ≈ 0.85  
  - F1 macro ≈ 0.83  
  - ROC-AUC macro ≈ 0.87  
  - PR-AUC macro ≈ 0.80  
- El kernel RBF superó al lineal en todas las métricas, aunque con menor interpretabilidad.

### Comparación NB vs SVM
| Modelo        | Accuracy | F1 Macro | ROC-AUC | PR-AUC | Interpretabilidad |
|---------------|----------|----------|---------|--------|------------------|
| GaussianNB    | ~0.80    | ~0.78    | ~0.82   | ~0.75  | Baja (supuestos violados) |
| BernoulliNB   | ~0.79    | ~0.77    | ~0.81   | ~0.74  | Baja |
| SVM Lineal    | ~0.82    | ~0.80    | ~0.84   | ~0.77  | Alta (pesos w) |
| SVM RBF       | ~0.85    | ~0.83    | ~0.87   | ~0.80  | Baja |

---

## ✅ Conclusiones
- **Naïve Bayes** es rápido y simple, pero sensible a correlaciones entre predictores.  
- **SVM lineal** ofrece interpretabilidad y buen rendimiento.  
- **SVM RBF** logra el mejor desempeño global, recomendado si la prioridad es maximizar métricas de clasificación.  
- La calibración de probabilidades mejora la confiabilidad de las predicciones en ambos enfoques.
