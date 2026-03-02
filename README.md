<img width="1308" height="756" alt="image" src="https://github.com/user-attachments/assets/e8f2fdc2-4319-4575-ab7c-3cd2a121863c" />


# 📊 ETF Predictor — IBEX 35 Signal Generator

> **Machine Learning applied to Financial Markets**
> Sistema integral diseñado para predecir la dirección y el retorno semanal del ETF **iShares IBEX 35 UCITS ETF (EXS1.DE)**.

---

## 🎯 Objetivo del Proyecto
Generar señales de trading automáticas basadas en modelos avanzados de **Gradient Boosting (XGBoost)**, analizando indicadores técnicos, correlaciones globales y la estructura temporal del mercado español.

### ⚡ Salidas del Modelo
* **Dirección:** `BUY` | `SELL` | `HOLD`
* **Niveles Operativos:** Precio de entrada, Stop-Loss dinámico y Take-Profit optimizado.
* **Gestión de Capital:** Cálculo automático del tamaño de la posición basado en riesgo.

---

## 🚀 Arquitectura del Sistema
El flujo de trabajo se divide en **5 fases modulares**, implementadas en notebooks independientes:

| Fase | Módulo | Descripción |
| :--- | :--- | :--- |
| **01** | 📥 **Data Acquisition** | Descarga de datos históricos (`yfinance`) de EXS1.DE, ^IBEX, S&P 500, DAX, Oro, VIX, EUR/USD y Bono 10Y. |
| **02** | ⚙️ **Feature Engineering** | Creación de +30 indicadores técnicos (RSI, MACD, Bollinger, ATR) y aplicación de *lags* temporales. |
| **03** | 🧠 **Model Training** | Entrenamiento dual: **XGBoost Classifier** (dirección) y **XGBoost Regressor** (magnitud). |
| **04** | 📡 **Signal Generator** | Motor de ejecución que calcula probabilidades y niveles de salida con gestión de riesgo. |
| **05** | 🖼️ **Visual Dashboard** | Informe gráfico con métricas de rendimiento, confianza del modelo y estado del mercado. |

---

## 🛠️ Stack Tecnológico

| Categoría | Herramientas |
| :--- | :--- |
| **Lenguaje** | `Python 3.10+` |
| **Machine Learning** | `XGBoost`, `Scikit-learn` |
| **Análisis de Datos** | `Pandas`, `NumPy` |
| **Finanzas** | `yfinance`, `pandas-ta`, `ta` |
| **Visualización** | `Matplotlib`, `Panel` |

---

## 📈 Características Clave

### 🧠 Modelado Dual (Hybrid Approach)
El sistema no solo predice si el mercado subirá, sino **cuánto**. 
* **Clasificador:** Filtra la dirección con mayor probabilidad.
* **Regresor:** Estima la volatilidad esperada para ajustar el Take-Profit.

### 🛡️ Gestión de Riesgo Profesional
* **Stop-Loss Dinámico:** Basado en el **ATR** (Average True Range) para adaptarse a la volatilidad real.
* **Risk/Reward:** Ratio mínimo configurado en $1.5$.
* **Anticipación:** Uso de *TimeSeriesSplit* para evitar el *data leakage* (uso de información del futuro).

---

## 📋 Instalación y Requisitos

Asegúrate de tener un entorno limpio y ejecuta:

```bash
pip install yfinance==0.2.38 \
            pandas-ta==0.4.71b0 \
            ta==0.11.0 \
            xgboost==2.0.3 \
            matplotlib pandas numpy
```
## 🖥️ Guía de Uso

🔄 Ciclo de EntrenamientoSi es la primera vez que usas el sistema, ejecuta los notebooks en este orden:01_data_extraction.ipynb02_feature_engineering.ipynb03_model_training.ipynb

## 📅 Operativa Semanal
Tras el cierre del mercado los viernes, genera tu estrategia para la semana siguiente:
Actualizar datos: Ejecuta el generador de señales.Consultar Dashboard: Revisa la confianza de la señal antes de operar.Tiempo estimado: ~3 minutos.

## 📊 Métricas de Evaluación
El rendimiento se mide bajo criterios estrictos de la industria: 
Accuracy & ROC-AUC: Para validar la precisión de la dirección.
MAE & $R^2$: Para la precisión del retorno esperado.

## Aviso Legal: Este sistema es una herramienta de análisis basada en Machine Learning. Los mercados financieros implican riesgo. Resultados pasados no garantizan rendimientos futuros.
