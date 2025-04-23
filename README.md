# 🎧 Podcast Listening Time Prediction

This project aims to predict the **Listening Time (in minutes)** for podcast episodes using machine learning regression techniques. We build models using features like episode length, sentiment, host/guest popularity, and more.

---

## 📌 Problem Statement

The objective is to **predict how long a user will listen to a podcast episode**, based on various features available before the episode is published. This can help content platforms:
- Optimize ad placement
- Recommend content more effectively
- Better understand what factors impact listener engagement

---

## 📊 Dataset Overview

We used two datasets: `train.csv` and `test.csv`.

**Features in the dataset:**
- `Podcast_Name`, `Episode_Title`
- `Episode_Length_minutes`
- `Host_Popularity_percentage`, `Guest_Popularity_percentage`
- `Genre`, `Publication_Day`, `Publication_Time`
- `Number_of_Ads`
- `Episode_Sentiment`
- Target: `Listening_Time_minutes` (only in train set)

---

## 🧹 Data Preprocessing

- **Missing Values Handling:**
  - Imputed `Guest_Popularity_percentage` using `Host_Popularity_percentage` and a combined logic.
  - Added a new column `Popular_Level` as a categorical replacement.
- **One-Hot Encoding** for categorical features.
- **Outlier Detection**: Identified and addressed extreme values in `Episode_Length_minutes`.
- **Feature Selection**: Used model-based importance to drop less useful features.

---

## 📈 Exploratory Data Analysis (EDA)

- Analyzed the distribution of popularity, sentiment, publication time/day.
- Identified potential correlations between listening time and various features.
- Visualized impact of popularity levels and episode length.

---

## 🤖 Models Used

| Model                  | RMSE (Lower is Better) |
|-----------------------|------------------------|
| Linear Regression      | 10.14                  |
| Ridge Regression       | 10.14                  |
| Random Forest Regressor| 10.65                  |
| Gradient Boosting      | **9.97**               |
| XGBoost                | 9.98                   |
| LightGBM               | 9.98                   |

✅ **Gradient Boosting Regressor** performed the best after hyperparameter tuning.

---

## 🛠️ Hyperparameter Tuning

Used `GridSearchCV` for tuning the following Gradient Boosting parameters:

```python
{
  'subsample': 0.8,
  'n_estimators': 300,
  'min_samples_split': 2,
  'min_samples_leaf': 1,
  'max_depth': 6,
  'learning_rate': 0.1
}
