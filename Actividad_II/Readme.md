
# MACHINE LEARNING II — ACTIVIDAD II  
## Predicción de Churn en Clientes  
### **Autores: Marcelo Carmona — Paula Álvarez**

---

## 📌 Descripción del Proyecto

Este repositorio contiene el desarrollo completo de la **Actividad II** del curso **Machine Learning II**, cuyo objetivo es aplicar técnicas de modelamiento supervisado para la **predicción de churn** en un dataset real de clientes.

A lo largo del proyecto se realizan:

- Preprocesamiento y limpieza del dataset  
- Entrenamiento de modelos base  
- Optimización de modelos mediante **Random Search**  
- Análisis de varianza y estabilidad del Random Forest  
- Uso de **pesos por clase** para tratar el desbalance  
- Comparación entre modelos  
- Evaluación con métricas de clasificación y curvas ROC / PR  
- Conclusiones técnicas y de negocio  

---

## 🎯 Objetivos del Análisis

1. Preparar adecuadamente un dataset de churn (variables categóricas + numéricas).  
2. Entrenar modelos base: Árbol de decisión y Random Forest.  
3. Optimizar Random Forest mediante **RandomizedSearchCV**.  
4. Estudiar la reducción de varianza variando el número de árboles.  
5. Evaluar métricas clave:
   - Accuracy
   - Precision
   - Recall
   - F1-score
   - ROC-AUC
   - PR-AUC
6. Analizar diferencias entre modelos lineales, árboles y ensambles.  
7. Realizar un análisis crítico de desempeño y aplicabilidad.  

---

## 🔧 Tecnologías Utilizadas

- **Python 3.10+**  
- **scikit-learn**  
- **pandas, numpy**  
- **matplotlib, seaborn**  
- **Jupyter Notebook**  

---

## 📊 Resultados Principales

### 🔹 Comparación entre modelos con `class_weight="balanced"`

| Modelo                      | Accuracy | Precision | Recall | F1   | ROC-AUC | PR-AUC |
|----------------------------|----------|-----------|--------|------|---------|--------|
| Árbol de decisión          | 0.7138   | 0.4603    | 0.4492 | 0.4547 | 0.6300 | 0.3548 |
| Random Forest Optimizado   | **0.7692** | **0.5556** | **0.6551** | **0.6012** | **0.8358** | **0.6423** |

---

## 🧠 Conclusiones Principales

- El **Random Forest optimizado** supera ampliamente al Árbol de decisión.  
- La varianza disminuye significativamente al aumentar los árboles, validando la teoría del bagging.  
- En churn, la métrica más relevante es **PR-AUC**, debido al desbalance de clases.  
- Para estrategias de retención, el modelo con mayor Recall y PR-AUC (Random Forest) es el más adecuado.  
- El árbol individual es útil para interpretación, pero su desempeño es insuficiente.  

---
