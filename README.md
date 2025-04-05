# Time-series-Modeling-of-EU-Energy-Market

### Abstract


The increasing integration of renewable energy sources in European markets has resulted in frequent occurrences of negative electricity prices, posing challenges for market stability and profitability. This study presents a predictive framework that utilizes Long Short-Term Memory (LSTM), Seasonal Autoregressive Integrated Moving Average (SARIMA), and extreme Gradient Boosting (XGBoost) to analyze the duration and recovery of negative price events. By leveraging historical electricity price data, the model improves forecasting accuracy, enabling energy stakeholders to enhance risk management and strategic planning. Among the approaches explored, LSTM demonstrated strong predictive performance, effectively capturing temporal dependencies in electricity price fluctuations. The results highlight the potential of advanced machine learning and time series models in mitigating risks associated with negative price events, contributing to a more resilient and sustainable energy market.

### Methodology

The methodology for this study follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) framework, which is widely used for structured data mining projects. 
The CRISP-DM framework consists of six main phases: Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, and Deployment. Below is a breakdown of how each phase is applied in this study:

### Business Understanding:

The principal objective of this study is to design a comprehensive and effective predictive framework for identifying and analyzing negative electricity price events within the European energy market. The study focuses on improving the accuracy of forecasts and conducting an in-depth exploration of the factors that influence the onset, duration, and recovery of such events. By generating actionable insights, this research aims to strengthen risk management practices and promote the stability and resilience of energy markets. This is particularly critical given the increasing integration of renewable energy sources, and the findings are intended to support informed decision-making among market participants and policymakers while addressing the challenges posed by price volatility.

### Data Understanding:

This study utilizes the European Union Energy Market Data dataset, which consists of electricity price records across multiple European countries, covering various timestamps. Key attributes include date, hour, country, price (in EUR per MWh), energy type (green or non-green), and currency type. Preliminary exploration revealed several important characteristics and anomalies. The is-green-energy attribute serves as a binary indicator, identifying whether the energy source is classified as green. The hour attribute is within the valid range of 1 to 24, ensuring proper time representation. Notably, negative price values are present, indicating market conditions where electricity prices drop below zero. Additionally, the currency-type attribute consists of values 1 and 2, corresponding to EUR and USD, respectively. The dataset initially contained the date attribute in an object format, which was converted to a datetime format for enhanced usability. No missing values were identified, ensuring data completeness.

Feature selection and refinement were crucial in preparing the dataset for analysis. The data-source and last-updated attributes were removed as they did not contribute to predictive modeling. To maintain data consistency, records with non-EUR currency were discarded since USD pricing was only relevant for the United Kingdom. Furthermore, the EU-country attribute was mapped to corresponding country names, and records labeled as 'System' or 'Unknown' were excluded. These adjustments ensured that the dataset contained only relevant and interpretable information.

Electricity price trends varied significantly across countries for the same day and hour, reinforcing the necessity of focusing on a single market for precise modeling. Among all countries, Denmark exhibited price trends closely aligned with the overall market average, making it an ideal candidate for forecasting. This observation is evident in Figure 1, which compares the average monthly price trends of all countries, and Figure 2, which presents the total average of these countries. Denmark's trend closely follows the overall market pattern, further validating its selection. Additionally, Denmark recorded the highest number of negative price occurrences, with 1,198 cases, highlighting the need for an accurate predictive model.

### Figure 1:

<img src="figure1.png">

### Figure 2:

<img src="figure2.png">

Green energy sources played a significant role in negative pricing events, particularly in the Netherlands, France, and Austria. A comparative analysis of green and non-green energy prices showed that green energy had an average price of 40.96 EUR/MWh, whereas non-green energy was priced higher at an average of 45.30 EUR/MWh. The dataset also contained multiple price records per hour, potentially due to different price zones or market segments, necessitating aggregation for accurate modeling.

Several extreme values or outliers were observed within the dataset. However, given that these extreme price points could represent valid high/low prices due to market fluctuations such as supply \& demand, inflation, or energy crises, we decided to retain them. Additionally, some of these outliers could be seasonal, such as winter or summer spikes in energy demand, and might carry valuable information for forecasting future price trends.

In this study, we aslo analyzed the dynamics of negative electricity prices, focusing on their duration and recovery. The data revealed several significant trends. Negative prices typically do not last long, with most data points concentrated around low durations. When negative prices persist for longer periods, the prices tend to remain low even after the negative period has ended. Additionally, extreme price spikes are often observed when the negative price duration is zero, which suggests that high prices are typically associated with periods where negative prices do not occur at all.

Moreover, we found that higher electricity prices correlate with higher price volatility, where price swings become more pronounced during periods of high prices. In contrast, when prices are very low, including negative prices, volatility tends to remain relatively stable, with less dramatic fluctuations. Interestingly, price spikes above 1000 EUR/MWh were associated with extremely high volatility, indicating sudden and unpredictable price changes. These observations are essential for understanding the underlying behavior of electricity prices and their volatility, especially in the context of forecasting negative price events.

### Data Preparation:

To enhance data management and ensure consistency, the column names in the dataset were standardized. The original column names were renamed to more intuitive labels, improving readability and ease of use. Specifically, the column fecha was renamed to date, hora to hour, sistema to EU-country, bandera to is-green-energy, precio to price-eur-per-mwh, tipo-moneda to currency-type.

To address the presence of multiple records per hour, data aggregation was performed to obtain a single representative price per timestamp. The dataset was grouped by date and hour, computing key statistics such as the mean electricity price, the maximum indicator for negative prices, the longest duration of negative pricing within the hour, and the highest recorded green energy indicator. This ensured that the aggregated dataset accurately captured essential market dynamics while minimizing redundancy.

Feature engineering played a pivotal role in enhancing forecasting accuracy. Several time-based features were introduced, including the month, day of the week, and a binary indicator for weekdays to capture seasonal and weekly consumption patterns. Sine and cosine transformations of the hour attribute were applied to effectively model the cyclical nature of electricity prices. Additionally, price-based features were engineered, such as price lags (1-hour, 2-hour, and 3-hour), rolling averages (7-day and 30-day), hourly price differences, and price volatility over 24-hour and 7-day periods. These features provided valuable insights into short-term fluctuations and long-term price stability.

To further improve predictive performance, target-specific features were introduced. A binary indicator for negative price occurrences helped identify critical market conditions, while the negative price duration feature captured how long negative pricing persisted. These attributes were essential for modeling recovery patterns and understanding prolonged negative price events. By applying these comprehensive data preparation techniques, the dataset was transformed into a structured format, ensuring optimal forecasting accuracy and enabling robust insights into negative price fluctuations in the Danish electricity market.
