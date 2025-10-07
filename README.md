# 🧭 Manual de Ejecución — Trabajo Final Grupo O (JupyterLab)

Este documento explica **cómo ejecutar correctamente el archivo `TrabajoFinal_GrupoO.ipynb`** paso a paso, tanto en **JupyterLab**, **VS Code**, como en **Google Colab**.  

El notebook desarrolla un flujo completo de **análisis de datos y machine learning** sobre el dataset **IBM HR Analytics Employee Attrition**, que puede descargarse desde Kaggle.

---

## ⚙️ Requisitos e instalación de dependencias

El proyecto requiere las siguientes librerías de Python, listadas en el archivo **`requirements.txt`**.

Para instalarlas automáticamente, ejecutar en una terminal (desde la carpeta del proyecto):

```bash
pip install -r requirements.txt
```

### 💡 En caso de no tener instalado JupyterLab o las librerías necesarias:
Ejecutar los siguientes comandos manualmente:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn jupyterlab ipykernel
```

Una vez completada la instalación, se podrá abrir y ejecutar el notebook sin inconvenientes.

---

## 📦 1. Descargar el dataset

**Dataset oficial:**
👉 [IBM HR Analytics Employee Attrition Dataset — Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data)

Una vez descargado, obtendrás un archivo llamado:

```
WA_Fn-UseC_-HR-Employee-Attrition.csv
```

### Recomendación:
- Crear una carpeta llamada `data` dentro del proyecto.  
- Colocar allí el archivo CSV descargado.  
  Ejemplo:
  ```
  /TrabajoFinal_GrupoO/
  ├── data/
  │   └── WA_Fn-UseC_-HR-Employee-Attrition.csv
  └── TrabajoFinal_GrupoO.ipynb
  ```

---

## 🧰 2. Abrir y ejecutar el notebook

Podés abrir el archivo de tres maneras:

### 🔹 Opción A — **JupyterLab**
```bash
jupyter lab
```
Luego abrí `TrabajoFinal_GrupoO.ipynb` y seleccioná  
**Kernel → Restart Kernel and Run All Cells** (para ejecutar todo automáticamente).

### 🔹 Opción B — **VS Code**
1. Abrí la carpeta del proyecto.  
2. Asegurate de tener instalada la extensión **Python** y **Jupyter**.  
3. Abrí el archivo `.ipynb`.  
4. Podés ejecutar celda por celda o con **Run All** (botón ▶️ arriba del notebook).

### 🔹 Opción C — **Google Colab**
- Subí el archivo `.ipynb` a tu Google Drive.  
- Abrilo con Google Colab.  
- Subí el dataset o conectá tu Drive para leerlo desde `/content/drive/MyDrive/...`.

---

## 🧩 3. Orden recomendado de ejecución (si no usás "Run All")

Si preferís ejecutar manualmente las celdas una por una, seguí este orden:

### **Paso 1 — Importación de librerías**
Ejecutá la primera celda con los `import` de librerías (`pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`, etc.).  
Esto carga las dependencias necesarias.

---

### **Paso 2 — Carga del dataset**
El notebook carga el archivo CSV principal.  
Asegurate de que la ruta del archivo esté correctamente configurada.

Si necesitás **cambiar la ruta manualmente**, seguí estos pasos:

1. En **VS Code** o el Explorador de archivos, hacé clic derecho sobre el archivo CSV.  
2. Seleccioná **“Copiar ruta”** (o “Copy Path”).  
3. Pegá esa ruta en el código, por ejemplo:

```python
import pandas as pd
df = pd.read_csv(r"C:\Users\TuUsuario\Desktop\TrabajoFinal_GrupoO\data\WA_Fn-UseC_-HR-Employee-Attrition.csv")
```

> ⚠️ Asegurate de mantener la `r` antes de las comillas para evitar errores con las barras invertidas en Windows.

---

### **Paso 3 — Exploración inicial (EDA)**
Aquí se analizan las columnas, tipos de datos, valores nulos, estadísticas y visualizaciones iniciales del dataset.

- Uso de `df.info()`, `df.describe()`, `df.isna().sum()`  
- Gráficos exploratorios con `seaborn` y `matplotlib`

---

### **Paso 4 — Proceso ETL (Limpieza y transformación)**
En esta sección se:
- Elimina o rellena valores faltantes.  
- Convierte variables categóricas a numéricas (One-Hot Encoding).  
- Escala o normaliza variables numéricas (StandardScaler).  
- Divide el dataset en **features (X)** y **target (y)**.  
- Realiza el `train_test_split`.

---

### **Paso 5 — Manejo del desbalance de clases**
El dataset tiene clases desbalanceadas en “Attrition” (sí/no).  
Se usa `imblearn` (por ejemplo `RandomUnderSampler`) para equilibrarlas antes del entrenamiento.

---

### **Paso 6 — Entrenamiento de modelos**
Se entrenan y comparan distintos modelos de machine learning, como:
- `LogisticRegression`
- `KNeighborsClassifier`
- `GaussianNB`
- `RandomForestClassifier`
- `GradientBoostingClassifier`
- `SVC`
- `MLPClassifier`

Cada uno se evalúa con métricas como:
- `accuracy_score`
- `f1_score`
- `roc_auc_score`
- `confusion_matrix`

---

### **Paso 7 — Evaluación y comparación de resultados**
Se grafican o muestran tablas comparativas con el rendimiento de cada modelo.  
También se pueden mostrar curvas ROC y matrices de confusión.

---

### **Paso 8 — Exportación de resultados**
Si el notebook genera resultados (por ejemplo, empleados con alto riesgo de renuncia), estos se guardan en CSV:

```python
df_empleados_riesgo.to_csv("outputs/empleados_en_riesgo.csv", index=False)
```

Si no existe la carpeta `outputs/`, crearla antes:

```python
from pathlib import Path
Path("outputs").mkdir(exist_ok=True)
```

---

### **Paso 9 — Conclusiones**
Al final del notebook se presentan conclusiones generales del análisis y del modelo con mejor desempeño.
