# Calidad Aire de Bucaramanga

## 1. Descripción del problema

Los altos niveles de **PM10, PM2.5, NO₂ y O₃** afectan la salud pública y la competitividad urbana de Bucaramanga. El proyecto busca **predecir en tiempo real dichos contaminantes** integrando variables meteorológicas (temperatura, lluvia, humedad, dirección y velocidad del viento, radiación solar) y temporales (hora, día, mes, día de la semana y día del año)[^1_1].

## 2. Conjunto de datos

- Fuente: Portal de Datos Abiertos de Colombia (dataset “Reporte Calidad de Aire – AMB”).
- Periodo: **2018–2020**.
- Estaciones usadas: *Lagos I Floridablanca, La Ciudadela, Santa Cruz Girón, San Francisco, Lagos del Cacique* (5 en total)[^1_1].
- Tamaño tras el pre-procesamiento: **84 120 registros × 12 columnas**[^1_1].


## 3. Metodología

1. **Pre-procesamiento**
    - Reorganización por estación y sello temporal.
    - Imputación KNN (k = 5) en variables meteorológicas con valores faltantes[^1_1].
    - *Label Encoding* para la estación y expansión de variables temporales.
2. **Modelado**
    - Árboles de decisión: **Random Forest** y **XGBoost** (100 árboles, *random_state*=42)[^1_1].
    - **Red neuronal** (PyTorch) de 3 capas ocultas con *BatchNorm* y *Dropout* 0.3.
    - **Algoritmo genético (DEAP)** para optimizar hiperparámetros de la red (población = 20, 6 generaciones)[^1_1].
3. **Evaluación**
    - Métricas: *MSE*, *MAE* y **R²**.
    - División específica *train/val/test* por contaminante debido a su diferente cantidad de registros[^1_1].

## 4. Requisitos e instalación

```bash
# 1. Clonar el proyecto
git clone https://github.com/Yandres25/CalidadAireBucaramanga.git
cd air-quality-bga

# 2. Instalar dependencias
pip install -r requirements.txt
```


### Principales dependencias

- pandas, numpy, scikit-learn
- xgboost
- torch, torchvision
- deap, tqdm, matplotlib, seaborn

## 5. Licencia

Proyecto liberado bajo la **MIT License**. Ver `LICENSE` para más detalles.

