# Telemetry Time Series Analysis (In Progress)

A friend at Norco Rocketry Club sent me hotfire telemetry data in the form of a raw CSV. This project analyzes rocket engine telemetry data using time series techniques to identify patterns, detect anomalies, and develop forecasting models. The work demonstrates core skills in time series preprocessing, exploratory data analysis (EDA), statistical modeling, and signal processing for aerospace applications.

## Project Overview

Rocket hotfire telemetry data consists of high-frequency time-stamped readings from engine sensors during static test firings. The goal of this project is to:
- Explore and visualize engine performance trends, oscillations, and noise characteristics
- Detect abnormal behavior in engine operation and sensor readings  
- Apply time series decomposition to understand underlying patterns
- Develop forecasting models using statistical and machine learning approaches

## Dataset Description

**Source**: Norco Rocketry Club hotfire test data
- **Data Structure**: SQLite database containing processed telemetry measurements
- **Time Range**: April 2025 sensor readings from rocket engine testing
- **Frequency**: Sub-second intervals (0.1-0.9 second increments)
- **Format**: Time-value pairs with ISO 8601 timestamp formatting

### Sample Data Structure
```
time                     value
2025-04-05T17:00:00.1Z   13.66520
2025-04-05T17:00:00.3Z   13.51391
2025-04-05T17:00:00.5Z   13.34281
```

## Current Progress

### ✅ Completed
- **Data Loading & Preprocessing**: SQLite extraction, timestamp parsing, data cleaning
- **Time Series Resampling**: Aggregated sub-second data to 1-second intervals
- **Initial Visualization**: Time series plots with rolling average smoothing
- **Seasonal Decomposition**: Additive decomposition showing trend, seasonal, and residual components
- **Stationarity Testing**: Augmented Dickey-Fuller test implementation

### 🔄 In Progress  
- **Enhanced EDA**: Statistical summaries, outlier detection, data quality assessment
- **ARIMA Modeling**: Automated parameter selection using pmdarima
- **Model Validation**: Performance metrics and cross-validation framework

### 📋 Planned Objectives
1. **Advanced Time Series Analysis**:
   - ARIMA / SARIMA modeling for forecasting
   - Autocorrelation and partial autocorrelation analysis
   - Model diagnostics and residual analysis

2. **Anomaly Detection** (Aerospace-focused):
   - Statistical methods for detecting engine anomalies
   - Threshold-based alerts for critical parameters
   - Pattern recognition for normal vs. abnormal engine behavior

3. **Signal Processing Applications**:
   - Frequency domain analysis for engine vibration patterns
   - Noise filtering and signal enhancement
   - Multi-sensor correlation analysis (if additional channels available)

## Tools and Libraries

- **Core Analysis**: `pandas`, `numpy`, `matplotlib`, `seaborn`
- **Time Series**: `statsmodels`, `pmdarima` for ARIMA modeling  
- **Database**: `sqlite3` for data management
- **Machine Learning**: `scikit-learn` for anomaly detection
- **Signal Processing**: `scipy` for frequency analysis (planned)

## Key Findings So Far

Initial analysis reveals:
- **High-frequency oscillations**: Characteristic of rocket engine combustion dynamics
- **Rapid value changes**: Typical sensor response during hotfire operations  
- **Periodic patterns**: Some evidence of cyclical behavior in engine parameters
- **Signal noise**: Sub-second measurements require smoothing for trend analysis

## Current Implementation

### Data Processing Pipeline
```python
# Load from SQLite database
df = pd.read_sql_query("SELECT * FROM telemetry_final;", conn)

# Preprocess timestamps and resample
df['time'] = pd.to_datetime(df['time'], format='ISO8601')
df.set_index('time', inplace=True)
df_resampled = df.resample('1S').mean()

# Apply smoothing and decomposition
df['rolling_mean'] = df['value'].rolling(window=10).mean()
result = seasonal_decompose(df['value'], model='additive', period=10)
```

## Repository Structure

```
├── Telemetry_Smoothed_TimeSeries.ipynb    # Main analysis notebook (current work)
├── telemetry.db                           # SQLite database (hotfire data)
├── README.md                              # Project documentation
└── data/                                  # Raw CSV files (original format)
```

## Research Applications

This project demonstrates practical time series analysis skills directly applicable to:
- **Aerospace Engineering**: Engine health monitoring and performance analysis
- **Signal Processing**: High-frequency sensor data analysis and noise reduction  
- **Predictive Maintenance**: Anomaly detection for critical system monitoring
- **Control Systems**: Understanding dynamic system behavior through data

The rocket telemetry context provides a compelling real-world application showcasing statistical modeling techniques on actual aerospace data.

---

**Status Note**: This project is actively being developed as part of my application materials for research opportunities. The aerospace domain provides an excellent demonstration of time series techniques applied to high-stakes engineering data, where accurate analysis and anomaly detection are critical for safety and performance.
