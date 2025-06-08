## 📊 1. `hyrox_ml` — Machine Learning Analysis

In this notebook, I dive deep into Hyrox race data to extract insights, build predictive models, and prepare data for later LLM fine-tuning:

### 📌 Disclaimer

The dataset used in this project was obtained by following the web scraping tutorial published here:  
🔗 [https://www.kaggle.com/code/jgug05/hyrox-data-scraping/notebook](https://www.kaggle.com/code/jgug05/hyrox-data-scraping/notebook)

All data was collected for educational purposes and is publicly available through the official Hyrox results website.

### 🔹 Data Preparation & Feature Engineering

* Loaded raw Hyrox race results for each athlete: segment times (runs + workout stations + roxzones).
* Converted time strings to numeric seconds for all columns.
* Created additional features:

  * **z-score normalized** times for each segment.
  * **Min-Max–scaled** times.
  * **Age binning**, **gender encoding**, and **cluster** of athletes profiles based on their performance.
  * **Aggregated summaries**: total time, work vs run split, residuals vs model predictions.

### 🔹 Exploratory Data Analysis (EDA)

* Visualized distributions and correlations between segment times and overall race time.
* Identified clusters of athlete types.
* Explored feature importance for insight into which exercises disproportionately impact total time.

### 🔹 Predictive Modeling

* Trained a **Linear Regression** model to establish baseline insights into exercise impact.
* Built a **LightGBM regression model** to capture non-linear relationships and improve total time prediction.
* Compared model performance using:

  * Mean Squared Error (MSE)
  * R² score
  * Feature importance breakdowns.

### 🔹 Performance Feedback Generation

* Calculated residuals (actual – predicted times).
* Created a `performance_feedback` field based on:

  * Segment timings that deviated significantly from prediction.
  * Cluster context and athlete metadata.
* Produced structured feedback sentences that highlight areas for improvement, aligned with later LLM fine-tuning.
