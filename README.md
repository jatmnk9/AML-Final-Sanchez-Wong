# 🎓 Capstone Project — Advanced Machine Learning

## Clasificación de Aceptabilidad de Vehículos mediante Redes Neuronales

**Estudiante:** Jatziry Sanchez Wong
**Profesor:** Carlos Mariño PhD.
**Fecha:** 02 de mayo del 2026

---

## 📋 Descripción del Proyecto

Este proyecto aborda el problema de **clasificación automática de la aceptabilidad de vehículos** en el mercado de segunda mano, utilizando el [Car Evaluation Database](https://archive.ics.uci.edu/dataset/19/car+evaluation) del UCI Machine Learning Repository (Bohanec & Rajkovic, 1997).

Se implementó una **red neuronal totalmente conectada (MLP)** con PyTorch, entrenada sobre representaciones ordinales de las variables categóricas. El modelo fue comparado con baselines clásicos (Regresión Logística y Random Forest).

### Resultados Principales

| Modelo                  | Accuracy | Precision | Recall  | F1 Weighted |
|-------------------------|----------|-----------|---------|-------------|
| **Random Forest**       | 96.92%   | 97.07%    | 96.92%  | 96.89%      |
| **MLP (Deep Learning)** | 96.15%   | 96.38%    | 96.15%  | 96.21%      |
| **Regresión Logística** | 74.23%   | 78.98%    | 74.23%  | 75.60%      |

> ✅ **Objetivo cumplido:** El modelo MLP supera el 95% de precisión en el conjunto de test.

---

## 📁 Estructura del Repositorio

```
AML-Final-Sanchez-Wong/
├── notebooks/
│   └── final_project.ipynb    # Notebook principal del proyecto (ejecutable en Colab)
├── data/
│   └── README.md              # Instrucciones y descripción del dataset
├── results/
│   ├── final_results.json     # Métricas finales del modelo MLP
│   ├── model_comparison.csv   # Comparación entre modelos
│   ├── feature_importances.csv
│   ├── car_evaluation_checkpoint.pth  # Pesos del modelo entrenado
│   ├── ordinal_encoder.pkl    # Encoder serializado
│   └── scaler.pkl             # Scaler serializado
├── figures/
│   ├── 01_target_distribution.png
│   ├── 02_features_by_class.png
│   └── ...                    # Visualizaciones generadas
├── report/
│   └── classification_report.txt  # Reporte de clasificación detallado
├── src/                       # Código auxiliar (opcional)
├── requirements.txt           # Dependencias del proyecto
└── README.md                  # Este archivo
```

---

## 🚀 Cómo Ejecutar

### Opción 1: Google Colab (Recomendado)

1. Ir a la carpeta `notebooks/`
2. Abrir `final_project.ipynb`
3. Hacer clic en **"Open in Colab"**
4. Ejecutar todas las celdas en orden

> El notebook descarga automáticamente el dataset desde UCI ML Repository — no es necesario descargar datos manualmente.

### Opción 2: Local

```bash
# Clonar el repositorio
git clone https://github.com/tu-usuario/AML-Final-Sanchez-Wong.git
cd AML-Final-Sanchez-Wong

# Instalar dependencias
pip install -r requirements.txt

# Abrir el notebook
jupyter notebook notebooks/final_project.ipynb
```

---

## 📊 Dataset

- **Fuente:** [Car Evaluation — UCI ML Repository (ID=19)](https://archive.ics.uci.edu/dataset/19/car+evaluation)
- **Instancias:** 1,728
- **Features:** 6 atributos categóricos ordinales
- **Clases:** 4 (unacc, acc, good, vgood)
- **Desbalance:** Ratio máx/mín de 18.6:1

> ⚠️ El dataset **no** se sube al repositorio. Se carga automáticamente con la librería `ucimlrepo`.

Para más detalles, ver [`data/README.md`](data/README.md).

---

## 🧠 Arquitectura del Modelo

**MLP (Perceptrón Multicapa)** implementado en PyTorch:

```
Input (6) → Dense(128) + ReLU + Dropout(0.3)
          → Dense(64)  + ReLU + Dropout(0.3)
          → Dense(32)  + ReLU + Dropout(0.3)
          → Output(4)  + Softmax
```

**Hiperparámetros:**
- Optimizador: Adam (lr = 0.001)
- Batch size: 32
- Épocas: 100
- Semilla aleatoria: 42

---

## 📝 Reproducibilidad

- ✅ Semilla aleatoria fija (`RANDOM_SEED = 42`)
- ✅ Dataset descargado automáticamente desde UCI
- ✅ Métricas exportadas a `results/`
- ✅ Visualizaciones exportadas a `figures/`
- ✅ Reporte de clasificación exportado a `report/`
- ✅ Modelos y encoders serializados en `results/`

---

## 📚 Referencias

- Bohanec, M. & Rajkovic, V. (1997). Car Evaluation. UCI Machine Learning Repository. https://archive.ics.uci.edu/dataset/19/car+evaluation
- PyTorch Documentation. https://pytorch.org/docs/
- scikit-learn Documentation. https://scikit-learn.org/stable/
