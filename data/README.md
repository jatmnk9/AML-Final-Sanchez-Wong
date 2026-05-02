# Data

## Car Evaluation Dataset — UCI Machine Learning Repository

> ⚠️ **Nota:** El dataset no se incluye directamente en este repositorio. Se descarga automáticamente desde el UCI Machine Learning Repository al ejecutar el notebook.

### Fuente

- **Repositorio:** [UCI Machine Learning Repository — Car Evaluation (ID=19)](https://archive.ics.uci.edu/dataset/19/car+evaluation)
- **Enlace directo al CSV:** https://archive.ics.uci.edu/static/public/19/data.csv
- **Donado por:** Marko Bohanec & Blaz Rajkovic (1997-05-31)

### Descripción

El dataset contiene **1,728 instancias** con **6 atributos categóricos ordinales** y **1 variable objetivo** (`class`) con 4 categorías de aceptabilidad de vehículos.

| Variable   | Tipo               | Valores posibles              | Descripción                        |
|------------|--------------------|------------------------------ |------------------------------------|
| `buying`   | Categórica ordinal | vhigh, high, med, low         | Precio de compra del vehículo      |
| `maint`    | Categórica ordinal | vhigh, high, med, low         | Precio de mantenimiento            |
| `doors`    | Categórica ordinal | 2, 3, 4, 5more                | Número de puertas                  |
| `persons`  | Categórica ordinal | 2, 4, more                    | Capacidad de personas              |
| `lug_boot` | Categórica ordinal | small, med, big               | Tamaño del maletero                |
| `safety`   | Categórica ordinal | low, med, high                | Nivel de seguridad estimado        |
| `class`    | Categórica (target)| unacc, acc, good, vgood       | Nivel de aceptabilidad del vehículo|

### Distribución de clases

| Clase   | Frecuencia | Porcentaje |
|---------|------------|------------|
| unacc   | 1,210      | 70.02%     |
| acc     | 384        | 22.22%     |
| good    | 69         | 3.99%      |
| vgood   | 65         | 3.76%      |

**Ratio de desbalance (máx/mín):** 18.6:1

### Cómo cargar los datos

El notebook descarga automáticamente el dataset usando la librería `ucimlrepo`:

```python
from ucimlrepo import fetch_ucirepo
car_evaluation = fetch_ucirepo(id=19)
X = car_evaluation.data.features
y = car_evaluation.data.targets
```

### Notas de preprocesamiento

- **Sin valores faltantes** — Confirmado por el análisis exploratorio.
- **Sin duplicados** — Todos los registros son únicos.
- **Codificación:** Se utilizó codificación ordinal (`OrdinalEncoder` de scikit-learn), aprovechando la naturaleza ordinal inherente de las 6 variables.
- **Estandarización:** Se aplicó `StandardScaler` tras la codificación ordinal.
- **División:** 85% entrenamiento / 15% test, con semilla aleatoria fija (`RANDOM_SEED=42`).