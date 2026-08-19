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

##  Evaluación de Modelos (Partición Train 70% / Test 30%, `class_weight='balanced'`)

| Modelo de Machine Learning | Accuracy en Test | Recall clase 1 (en riesgo) | ROC-AUC |
| :--- | :---: | :---: | :---: |
|  **Regresión Logística** | **49.60%** | **48%** | **0.4965** |
|  **Random Forest Regulado** | **54.70%** | **39%** | **0.5152** |
|  **Árbol de Decisión (`max_depth=5`)** | **54.32%** | **32%** | **0.4908** |

>  **Bug corregido:** la versión anterior de este repo no usaba `class_weight='balanced'`. Con el target desbalanceado (64%/36%), los 3 modelos colapsaban a predecir *siempre* la clase 0 ("sin riesgo") — 0% de recall en la clase 1, es decir, el modelo nunca detectaba un paciente en riesgo sin importar sus datos. Eso explicaba la accuracy "buena" (64%) que en realidad solo eran modelos prediciendo la clase mayoritaria. Ya está corregido: el modelo balanceado en `heart_attack_model.joblib` ahora sí predice la clase 1 en una proporción razonable.
>
> **Limitación real del dataset (no corregible con código):** la correlación máxima entre cualquier feature clínica y `Heart Attack Risk` es 0.019 (prácticamente cero), y el ROC-AUC de los 3 modelos es ~0.49–0.52 — equivalente a azar. Este dataset de Kaggle en particular no parece tener una relación causal real entre las variables de salud y la etiqueta, por lo que ningún modelo entrenado sobre él va a predecir riesgo cardíaco de forma confiable. Ver la sección de limitaciones en el notebook para más detalle.

---

##  Cómo Ejecutar el Código

Abre PowerShell o CMD y ejecuta:

```bash
python C:\Users\juanp\Downloads\heart_attack_analysis.py
```
