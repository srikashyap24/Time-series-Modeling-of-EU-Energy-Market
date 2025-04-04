Time-Series Modeling of Negative PriceDuration and Recovery in EU Energy Markets

Project Overview:
The increasing share of renewable energy in European markets has led to frequent occurrences of negative electricity prices. This project develops a predictive framework using SARIMA, LSTM, and XGBoost to analyze the duration and recovery of negative price events. By leveraging historical data, the time series modeling enhances forecasting accuracy, aiding energy stakeholders in risk management and strategic planning. A comparison of the three models was conducted, and LSTM demonstrated the best performance.

Files in the Project:
1. project.ipynb - Contains data cleaning, preprocessing, exploratory data analysis (EDA), and the SARIMA model implementation.
2. XGBoost.ipynb - Implements the XGBoost model for predicting negative price events.
3. LSTM.ipynb - Implements the LSTM model for time-series forecasting.
4. EU_energy_data.csv - The original dataset containing energy market data for European countries.
5. denmark_data.csv - Filtered dataset containing only Denmark's energy market data.
6. denmark_data_new.csv - Dataset after feature engineering applied to Denmark's data.
7. lstm_model.h5 - Saved LSTM model file.

Methodology:
1.Data Preprocessing
a) Used EU_energy_data.csv to perform data cleaning, preprocessing, and EDA in project.ipynb.
b) Denmark-specific data was selected, creating denmark_data.csv.
c) Feature engineering was applied to denmark_data.csv, resulting in denmark_data_new.csv.
2. Model Implementations and Evaluations
a) SARIMA: Implemented in project.ipynb to analyze and forecast price trends. The model was evaluated for accuracy.
b) XGBoost: Implemented in XGBoost.ipynb for predictive modeling and evaluated using relevant metrics.
c) LSTM: Implemented in LSTM.ipynb for deep learning-based time-series forecasting. The model was trained, tested, and evaluated using appropriate performance measures.
d) Model Comparison: The three models (SARIMA, XGBoost, and LSTM) were compared, and LSTM performed the best in terms of accuracy and predictive capability.
Usage
1. Run project.ipynb to preprocess data, perform EDA, and execute the SARIMA model.
2. Run XGBoost.ipynb to execute and evaluate the XGBoost model for predictions.
3. Run LSTM.ipynb to train, evaluate, and test the LSTM model using denmark_data_new.csv.
4. The trained LSTM model is saved as lstm_model.h5.

Author: Sri Kashyap Dongari & Akhil Goud Rachakonda

