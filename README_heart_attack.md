#  Predicción de Riesgo de Ataque al Corazón - Heart Attack Dataset

Este proyecto evalúa y predice el riesgo de ataque cardíaco (**`Heart Attack Risk`**) utilizando el dataset `heart_attack_prediction_dataset.csv` de 8,763 pacientes.

---

##  Archivos del Proyecto

* **Script Python**: [`heart_attack_analysis.py`](file:///C:/Users/juanp/Downloads/heart_attack_analysis.py)
* **Jupyter Notebook**: [`heart_attack_analysis.ipynb`](file:///C:/Users/juanp/Downloads/heart_attack_analysis.ipynb)
* **Modelo Exportado Joblib**: [`heart_attack_model.joblib`](file:///C:/Users/juanp/Downloads/heart_attack_model.joblib)
* **Dataset fuente**: `heart_attack_prediction_dataset.csv` (ubicado en `C:\Users\juanp\Downloads`)

---

##  Análisis Exploratorio de Datos (EDA)

1. **Dimensiones**: 8,763 registros y 26 columnas.
2. **Valores Nulos**: **0 datos faltantes** (dataset 100% completo).
3. **Distribución del Target (`Heart Attack Risk`)**:
   * **`0` (Bajo Riesgo / Sin Ataque)**: **5,624 pacientes (64.18%)**
   * **`1` (Alto Riesgo / Con Ataque)**: **3,139 pacientes (35.82%)**
4. **Ingeniería de Características (*Feature Engineering*)**:
   * Se separó la variable compuesta `Blood Pressure` (ej: `"158/88"`) en dos variables cuantitativas continuas: **`Systolic_BP`** (Presión Sistólica) y **`Diastolic_BP`** (Presión Diastólica).

---

##  Evaluación de Modelos (Partición Train 70% / Test 30%, `class_weight='balanced'`)

| Modelo de Machine Learning | Accuracy en Test | Recall clase 1 (en riesgo) | ROC-AUC |
| :--- | :---: | :---: | :---: |
|  **Regresión Logística** | **49.60%** | **48%** | **0.4965** |
|  **Random Forest Regulado** | **54.70%** | **39%** | **0.5152** |
|  **Árbol de Decisión (`max_depth=5`)** | **54.32%** | **32%** | **0.4908** |


---

##  Cómo Ejecutar el Código

Abre PowerShell o CMD y ejecuta:

```bash
python C:\Users\juanp\Downloads\heart_attack_analysis.py
```
