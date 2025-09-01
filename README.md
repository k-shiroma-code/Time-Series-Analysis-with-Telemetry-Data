# Telemetry Time Series Analysis (In Progress)

A friend at Norco Rocketry Club sent me hotfire telemetry data in the form of a raw csv. This project analyzes telemetry data using time series techniques to identify patterns, detect anomalies, and develop forecasting models. The work demonstrates core skills in time series preprocessing, exploratory data analysis (EDA), classical and deep learning modeling, and anomaly detection.

## Project Overview

Telemetry data consists of time-stamped readings from remote sensors or systems. The goal of this project is to:
- Explore and visualize trends, seasonality, and noise
- Detect abnormal behavior in system performance
- Forecast future values using statistical and machine learning models

## Dataset

- **Structure**:
  - `timestamp`: Date and time of the measurement
  - `sensor_id`: Identifier for the sensor/device
  - `value`: Measured reading (e.g., temperature, voltage, etc.)
  - Additional variables (if applicable): `location`, `status_flag`, etc.

## Objectives

1. Clean and preprocess the time series data
2. Perform exploratory analysis and time series decomposition
3. Apply forecasting models:
   - ARIMA / SARIMA
   - Facebook Prophet
   - LSTM (via TensorFlow/Keras)
4. Conduct anomaly detection using:
   - Statistical methods (z-scores, rolling averages)
   - Machine learning (Isolation Forest, Autoencoder)

## Tools and Libraries

- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `statsmodels`, `pmdarima` for ARIMA modeling
- `prophet` for generalized additive forecasting
- `scikit-learn` for anomaly detection
- `tensorflow.keras` for deep learning models

## Project Structure

| File/Notebook | Description |
|---------------|-------------|
| `01_eda.ipynb` | Data loading, cleaning, and exploratory analysis |
| `02_arima_modeling.ipynb` | Time series modeling using ARIMA and SARIMA |
| `03_lstm_modeling.ipynb` | Recurrent neural network modeling using LSTM |
| `04_anomaly_detection.ipynb` | Statistical and machine learning-based anomaly detection |


