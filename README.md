#  Railway Delay Analysis — Germany (Tübingen Hbf)

## Project Overview
This project analyzes train delays at **Tübingen Hauptbahnhof (Germany)** using one full year of railway operation data.  
The objective is to understand the structural drivers behind delays, explore the gap between passenger perception and official statistics, and evaluate how effectively delays can be modeled using Machine Learning.

The project combines **Exploratory Data Analysis (EDA)**, **hypothesis testing**, **regression**, and **classification**, progressing from descriptive insights to risk-oriented prediction.

---

## Motivation & Context
The motivation for this project comes from my personal experience living and commuting in the Tübingen region, where train delays are a recurring topic in daily passenger complaints.

While official statistics often report moderate average delays, passenger frustration remains consistently high.  
This project investigates that discrepancy and asks a central question:

> Why do delays feel worse than the numbers suggest?

By combining data analysis with real-world commuting patterns, the project aims to translate everyday passenger experience into measurable and actionable insights.

---

## Business & Analytical Questions
* Are delays mainly driven by rush hours, weekdays, or seasonal effects?
* Do different train types (regional vs. express) behave differently under congestion?
* Why do average delay metrics underestimate passenger frustration?
* Is predicting exact delay minutes feasible?
* Can a risk-based classification approach provide more reliable insights?
* Which factors increase the likelihood of **critical delays (> 5 minutes)**?

---

## Data Source
* One full year of train operation data from **Tübingen Hbf**
* Key variables include:
  * Delay duration (minutes)
  * Date and time features
  * Train type (regional, express, long-distance)
  * Final destination
* External operational causes (weather, construction, technical failures) are **not explicitly included**, which becomes a key modeling limitation.

---

## Methodology

### 1. Exploratory Data Analysis (EDA)
* Distribution of delay durations
* Rush hour vs. off-peak comparison
* Weekday and seasonal patterns
* Express vs. regional train behavior
* Route-level comparisons

### 2. Feature Engineering
* Temporal features: hour, day of week, month
* Rush hour indicator
* One-hot encoding for train types
* Label encoding for destinations (tree-based model compatible)

### 3. Regression Modeling
* **Random Forest Regressor**
* Goal: predict exact delay minutes
* Evaluation metrics: **MAE**, **R²**

### 4. Strategic Pivot to Classification
* Reframing the problem as:
  * **Critical delay prediction (> 5 minutes)**
* **Random Forest Classifier**
* Focus on operational relevance rather than minute-level precision

---

## Key Findings
* **The Monday Effect**  
  Hypothesis testing confirms that Mondays have significantly higher delays (*p < 0.05*), validating a common commuter perception.

* **Passenger Perception Gap**  
  Although the overall average delay is relatively low (~3 minutes), delayed trains during rush hours exceed 5 minutes on average, explaining persistent dissatisfaction.

* **Rush Hour Vulnerability**  
  Peak periods amplify delays, especially when trains are already late, compounding network instability.

* **Service-Type Differences**  
  Express services exhibit higher average delays than regional trains, suggesting stronger exposure to network-wide disruptions.

* **Spatial Bottlenecks**  
  Routes heading south from Tübingen show more consistent delay patterns than routes toward Stuttgart, challenging common assumptions.

---

## Modeling Results

### Regression (Exact Delay Prediction)
* **Mean Absolute Error (MAE):** 3.20 minutes  
* **R² Score:** -0.04  

Despite a reasonable MAE, the negative R² indicates poor explanatory power and highlights the instability of predicting exact delay minutes.

### Classification (Critical Delay > 5 Minutes)
* **Accuracy:** 82%  
* **Precision (on-time class):** 86%  
* **Recall (critical delay class):** 27%  

The classification model provides a more stable and interpretable framework, despite the difficulty of capturing rare but high-impact disruptions.

---

## Why Regression Failed — and Why That Matters
Exact delay prediction proved unreliable due to:
* High influence of unobserved external events (weather, technical issues, construction)
* Structural features explaining patterns, but not sudden disruptions

This insight motivated a shift toward **risk-based modeling**, which aligns more closely with real passenger decision-making.

---

## Limitations
* No weather or infrastructure maintenance data
* No real-time operational variables
* Class imbalance for critical delays

These limitations reflect real-world data constraints rather than modeling shortcomings.

---

## Strategic Implications

### For Passengers
The high precision of on-time predictions suggests that a real-time **punctuality risk alert** could meaningfully support travel planning, especially for long-distance connections.

### For Infrastructure Planning
Identified seasonal patterns and route bottlenecks highlight the need for targeted investments and improved winter resilience strategies.

---

## Next Steps
1. Integrate historical weather data (DWD)
2. Merge infrastructure and construction schedules
3. Develop a real-time prediction API (FastAPI)
4. Explore sequential models (RNNs / LSTMs) for temporal dependency learning
5. Design and implement a structured data pipeline for weather–infrastructure integration


---

## Final Notes
This project demonstrates how Data Science can transform everyday commuter frustration into structured, data-driven insights.  
Rather than focusing solely on prediction accuracy, it emphasizes **problem framing, analytical reasoning, and real-world relevance** — core skills for applied Data Science roles.
