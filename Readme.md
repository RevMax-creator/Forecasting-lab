# PM2.5 Forecasting Lab [web:62]

A repository for forecasting hourly PM2.5 concentrations using historical air quality data (PM2.5, PM10, NO2, O3) and weather variables (temperature, precipitation, cloud cover, etc.) from APIs such as Open‑Meteo.[web:62][web:64]  
The project compares classical machine learning baselines (Linear Regression, Decision Trees, k‑NN) with more advanced time series models (e.g., SARIMAX, LSTM, Transformers) for multi‑step forecasting.[web:66][web:69]  

## Project motivation [web:67]

Fine particulate matter (PM2.5) is strongly linked to respiratory and cardiovascular risks, so accurate short‑term forecasts help citizens and authorities plan exposure and interventions.[web:66][web:75]  
Machine learning and deep learning models can capture complex nonlinear relationships between meteorology, emissions, and pollutant concentrations better than simple heuristic methods.[web:66][web:78]  

## Objectives [web:62]

- Forecast hourly PM2.5 for the next 24–72 hours at a given location using historical air quality and weather data.[web:62][web:72]  
- Benchmark simple ML baselines (Linear Regression, DecisionTreeRegressor, KNeighborsRegressor) against more advanced models like gradient‑boosting, LSTM and Transformer‑based architectures.[web:66][web:69]  
- Evaluate performance using standard regression metrics (MAE, RMSE, MAPE, R²) and visualize actual vs predicted PM2.5 over time.[web:66][web:75]  

## Data sources [web:62]

- **Air quality data:** Hourly PM2.5, PM10, NO2, O3, and possibly AQI indices from open data APIs or platforms such as OpenAQ or local pollution control boards.[web:62][web:64]  
- **Weather data:** Hourly temperature, humidity, wind speed, wind direction, precipitation, cloud cover and related variables queried from APIs like Open‑Meteo.[web:65][web:68]  
- Data is merged on timestamp and location, cleaned for missing values/outliers, and optionally resampled to a fixed hourly grid.[web:61][web:69]  

## Repository structure [web:65]

- `notebooks/` – Exploratory analysis, feature engineering, and model training notebooks for each algorithm.[web:61][web:79]  
- `data/` – Processed datasets (or scripts/placeholders if raw data cannot be shared).[web:61][web:70]  
- `models/` – Saved model weights, scalers, and configuration files for trained models.[web:65][web:79]  
- `docs/` – Model‑specific documentation (`linear_regression.md`, `decision_tree.md`, `knn.md`, `transformer.md`, etc.).[web:67][web:73]  
- `src/` – Reusable Python modules for data loading, feature engineering, training, and evaluation (if you refactor notebooks into scripts).[web:65][web:79]  

## Feature engineering [web:69]

- Lag features: previous hours of PM2.5, PM10, NO2, O3 and key weather variables to convert the series into a supervised learning problem.[web:61][web:69]  
- Rolling statistics: moving averages, rolling min/max, and standard deviation windows to capture local trends and volatility.[web:66][web:78]  
- Temporal features: hour of day, day of week, holiday/weekend flags, and seasonal indicators to capture diurnal and weekly patterns.[web:69][web:78]  

## Models implemented [web:66]

- **Linear Regression:** Baseline linear model to estimate PM2.5 as a weighted combination of features.[web:21][web:69]  
- **Decision Tree Regressor:** Nonlinear tree‑based regressor that can capture feature interactions and thresholds.[web:17][web:66]  
- **k‑Nearest Neighbors Regressor:** Instance‑based method predicting PM2.5 from similar past conditions.[web:9][web:69]  
- **Ensemble tree models (optional):** Random Forest, Gradient Boosting, XGBoost, LightGBM for more powerful nonlinear baselines.[web:66][web:78]  
- **Time‑series/deep models (optional):** SARIMAX with exogenous variables, LSTM, 1D‑CNN, and Transformer models for sequence‑to‑sequence forecasting.[web:41][web:61]  

Each model has a dedicated documentation file in `docs/` describing assumptions, hyperparameters, and results.[web:67][web:73]  

## Training and evaluation pipeline [web:67]

- Data is split chronologically into training, validation, and test sets to avoid leakage from the future into the past.[web:69][web:78]  
- Time‑series cross‑validation (e.g., expanding window) is used to tune hyperparameters for the ML models.[web:69][web:78]  
- Models are evaluated using MAE, RMSE, MAPE, and R², with additional plots such as actual vs predicted time series and error distributions.[web:66][web:75]  

## How to run [web:67]

1. Clone the repository and create a Python environment with the required dependencies listed in `requirements.txt`.[web:67][web:73]  
2. Download or generate the processed dataset into the `data/` folder, or run the provided data‑collection script if available.[web:61][web:70]  
3. Open the notebooks in `notebooks/` and run them in order (EDA → feature engineering → model training → evaluation).[web:67][web:79]  
4. Refer to the model‑specific docs in `docs/` to understand configuration choices and interpret the results.[web:67][web:73]  

## Results summary [web:66]

- Early experiments typically show that simple linear models provide a strong baseline but struggle with nonlinear effects and sudden spikes.[web:66][web:69]  
- Tree‑based ensembles and deep learning models often reduce RMSE and better capture extreme PM2.5 episodes at the cost of higher complexity.[web:66][web:78]  
- Detailed metrics, plots, and model comparisons are reported in the `docs/` folder and final results notebook.[web:66][web:71]  

## Future work [web:72]

- Incorporate spatial information (multiple stations or grid cells) and explore graph‑based or attention‑based spatiotemporal models.[web:63][web:80]  
- Add more exogenous variables such as traffic, emissions inventories, and satellite‑based aerosol optical depth.[web:72][web:75]  
- Deploy the best model as an API or integrate it into a real‑time air‑quality monitoring app.[web:65][web:68]  
