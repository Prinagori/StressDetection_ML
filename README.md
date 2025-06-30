# 🧠 Stress Detection & Visualization with Power BI + Machine Learning

This project focuses on identifying and visualizing **stress levels in individuals using physiological data**. It combines Python-based preprocessing, **SMOTE-based machine learning models**, and interactive **Power BI dashboards** to communicate both model performance and data insights.

---

##  Problem Statement

Can we accurately detect psychological **stress** in individuals using biosensor signals such as **EDA (Electrodermal Activity)**, **HR** (Heart Rate), and **Temperature**, and visualize these predictions interactively?

---

##  Dataset

- Original source: A multivariate dataset with **EDA (Electrodermal Activity)**, **HR (Heart Rate)**, **TEMP**, and a binary `label` column (1 = Stress, 0 = No Stress).

> I initially tried:
>
> - A **stratified sampled dataset** (to balance the dashboard visually)
> - A **parquet version** (for performance)
>
> However, **Power BI had rendering issues** with both—especially in categorical and KPI visuals—so I used the **original dataset** in `.csv` format.

---

## Preprocessing Steps

- Removed null values, duplicates, and outliers
- Converted `label` to a categorical `Label Category` field:
- Applied **SMOTE** after train-test split to balance classes:
 
---

##  Machine Learning (Python)

- Models Tried: **Random Forest**, **XGBoost**
- Training was done on the **SMOTE-balanced training set**
- Testing was performed on the **original imbalanced test set** to reflect real-world data

###  Performance Summary:

| Model         | Accuracy | Recall (Stress) | Precision (Stress) |
| ------------- | -------- | --------------- | ------------------ |
| Random Forest | 0.95     | 0.97            | 0.87               |
| XGBoost       | 0.90     | 0.93            | 0.75              |

---


##  Insights

- **No Stress** label dominates (\~74% of the data)
- SMOTE significantly improved the model’s ability to detect minority class (Stress)
- Dynamic visuals helped reveal trends between HR/EDA/TEMP and stress levels

---

##  Future Improvements

### Power BI:

- Add anomaly thresholds using DAX
- Publish dashboard via Power BI Service for real-time filtering

### Machine Learning:

- Add feature importance visualization
- Tune XGBoost hyperparameters via cross-validation
- Deploy model via Flask or Streamlit

---

##  What I Learned

- How to handle large-scale biosignal data and correct class imbalance with SMOTE
- How model evaluation changes when tested on imbalanced data
- Integration limitations between Power BI and different data formats (sampled/parquet)
- Enhanced ability to combine data science outputs with business dashboards

