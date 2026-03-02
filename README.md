# 📊 ETF Predictor — IBEX 35 Signal Generator

Sistema integral de **Machine Learning aplicado a mercados financieros** diseñado para predecir la **dirección y el retorno semanal** del ETF  
**iShares IBEX 35 UCITS ETF (EXS1.DE)**.

El proyecto utiliza modelos avanzados de **Gradient Boosting con XGBoost** para analizar:

- Indicadores técnicos
- Activos globales correlacionados
- Estructura temporal del mercado

El resultado es la generación automática de señales de trading:

✔ Dirección (BUY / SELL / HOLD)  
✔ Precio de entrada  
✔ Stop-Loss dinámico  
✔ Take-Profit optimizado  
✔ Tamaño de posición basado en gestión de riesgo  

---

# 🚀 Arquitectura del Proyecto

El flujo de trabajo se divide en **5 fases modulares**, cada una implementada en un notebook independiente.

## 🔹 Fase 1 — Adquisición de Datos
Descarga automática de datos históricos semanales desde Yahoo Finance para:

- ETF principal: EXS1.DE  
- Índice de referencia: ^IBEX  
- Activos globales correlacionados:
  - S&P 500
  - DAX
  - Oro
  - Petróleo
  - VIX
  - EUR/USD
  - Bono Español 10Y

---

## 🔹 Fase 2 — Ingeniería de Features

Construcción de más de **30+ indicadores técnicos**, incluyendo:

- RSI
- MACD
- Bandas de Bollinger
- ATR
- Medias móviles (SMA / EMA)

Se aplican **lags temporales (retardos)** para capturar dependencias históricas sin necesidad de redes LSTM.

---

## 🔹 Fase 3 — Entrenamiento y Optimización

Implementación de dos modelos:

- **XGBoost Classifier** → Predicción de dirección (Sube/Baja)
- **XGBoost Regressor** → Predicción de magnitud del retorno esperado

Incluye:

- Optimización de hiperparámetros
- Validación temporal (TimeSeriesSplit)
- Prevención estricta de data leakage

---

## 🔹 Fase 4 — Generador de Señales

Carga de los modelos entrenados y generación automática de señal semanal:

- Probabilidad direccional
- Stop-Loss basado en ATR
- Take-Profit proporcional al riesgo
- Position sizing automático (% fijo del capital)

Tiempo de ejecución: < 2 minutos.

---

## 🔹 Fase 5 — Dashboard Visual

Generación de un informe visual que incluye:

- Señal actual
- Confianza del modelo
- Métricas de rendimiento
- Estado de indicadores clave
- Historial de señales

---

# 🛠️ Tecnologías Utilizadas

## 🐍 Lenguaje
- Python 3.10+

## 🤖 Machine Learning
- XGBoost (v2.0.3)
- Scikit-learn

## 📊 Análisis de Datos
- Pandas
- NumPy

## 📈 Indicadores Técnicos
- pandas-ta
- ta

## 💹 Datos Financieros
- yfinance (v0.2.38)

## 📉 Visualización
- Matplotlib
- Panel

---

# 📋 Requisitos e Instalación

Instala las dependencias necesarias:

```bash
pip install yfinance==0.2.38 pandas-ta==0.4.71b0 ta==0.11.0 xgboost==2.0.3 matplotlib pandas numpy
