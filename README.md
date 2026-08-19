#  Predicción de Riesgo de Ataque al Corazón - Heart Attack Dataset

Este trabajo evalúa y predice el riesgo de ataque cardíaco (**`Heart Attack Risk`**) utilizando el dataset `heart_attack_prediction_dataset.csv` de los 8,763 pacientes basado en el ejercicio que hicimos durante clase, donde usamos tambien un 70-30 de train test.

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
4. **Características**:
   * Se separó la variable compuesta `Blood Pressure` (ej: `"158/88"`) en dos variables cuantitativas continuas: **`Systolic_BP`** (Presión Sistólica) y **`Diastolic_BP`** (Presión Diastólica).

---

##  Evaluación de Modelos (Partición Train 70% / Test 30%)

| Modelo de Machine Learning | Accuracy en Train (CV) | Accuracy en Test (30% - 2,629 muestras) | ROC-AUC |
| :--- | :---: | :---: | :---: |
|  **Regresión Logística** | **64.18%** | **64.17%** | **0.4966** |
|  **Random Forest Regulado** | **64.18%** | **64.17%** | **0.5021** |
|  **Árbol de Decisión (`max_depth=5`)** | **64.16%** | **63.52%** | **0.4903** |

---

##  Cómo Ejecutar el Código

Abre PowerShell o CMD y ejecuta:

```bash
python C:\Users\juanp\Downloads\heart_attack_analysis.py
```
