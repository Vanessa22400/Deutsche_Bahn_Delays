# Railway Delay Risk Modeling – Tübingen (Germany)

Data-driven analysis of railway reliability using one full year of Deutsche Bahn operational data.

---

## Business Context

Reliable public transportation is essential for daily commuters. 

While living in the Tübingen region, I experienced frequent train delays that were constantly discussed among passengers. However, official statistics often reported only moderate average delays. This project began with a simple question:

If the numbers are moderate, why does the system feel unreliable?

Using one full year of operational data (Aug 2024 – Jul 2025), I analyzed structural delay patterns and evaluated how effectively disruptions can be modeled using Machine Learning.

---

## Problem Statement

- Can train delays be predicted using operational and temporal features?
- If predicting exact delay minutes proves unstable, can we instead identify high-risk delay scenarios?

---

## Objectives

- Identify structural drivers behind delays  
- Validate commuter perceptions through statistical testing  
- Model delay duration (regression)  
- Predict critical delays > 5 minutes (classification)  
- Translate findings into operational insight  

---

## Methodology

1. Data extraction via streaming (Hugging Face public DB dataset)  
2. Exploratory Data Analysis (temporal, service-type, and route patterns)  
3. Hypothesis testing (independent t-tests)  
4. Feature engineering (temporal variables + categorical encoding)  
5. Random Forest Regression  
6. Random Forest Classification  
7. Model evaluation and interpretation  

---

## Tools & Technologies

* Python (Pandas, NumPy)
* Scikit-learn
* SciPy (Hypothesis Testing)
* Statsmodels (Time-Series Decomposition)
* Random Forest (Regressor & Classifier)  
* Matplotlib
* Seaborn
* Folium (Geospatial Visualization)

---

## Exploratory Highlights


The analysis confirmed consistent structural patterns:

- A statistically significant **“Monday Effect”** (p ≈ 0.001)  
- Express services showing higher average delays than regional trains  
- Rush hours increasing both delay frequency and severity  
- Directional bottlenecks affecting specific routes 

These findings motivated formal hypothesis testing and modeling.

---

## Regression Results – Predicting Delay Duration

- Mean Absolute Error (MAE): 3.20 minutes  
- R² Score: -0.04 

The model performs reasonably for typical low-delay situations.  
However, extreme disruptions (often driven by external operational factors) make exact minute-level prediction unstable.

This limitation motivated a strategic pivot toward risk-based classification.

---

## Classification Results – Predicting Critical Delays (> 5 minutes)

![Feature Importance – Critical Delay Prediction](Images/6.Feature Importance.png)

- Accuracy: 82%  
- Precision (on-time class): 0.86  
- Recall (critical delay class): 0.27  

While extreme delays remain difficult to detect, the classification model provides a more stable and actionable framework for identifying delay risk.

---

## Key Insights

- The “Monday Effect” is statistically validated.  
- Seasonality is a stronger predictor than hour of departure.
- Express services carry structural vulnerability. 
- Average delay metrics underestimate passenger perception during peak hours.
- Southbound routes present stronger infrastructure bottlenecks than expected.  

---

## Business Applications

This analysis could support:

- Risk-based punctuality alerts for passengers  
- Seasonal planning and resource allocation  
- Identification of infrastructure bottlenecks  
- More transparent communication about network reliability  

---

## Conclusion

What started as a personal observation during my time commuting in Baden-Württemberg became a structured end-to-end analysis of railway performance.

The project demonstrates both the predictive potential and the structural limits of delay forecasting in a complex transport system—showing how data can bridge the gap between perception and operational reality.
