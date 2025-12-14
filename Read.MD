# 🫀 Heart Disease Risk Analytics: Insights & Prevention Guidelines

## 📌 Introduction

Cardiovascular diseases (CVDs) are currently the leading cause of death globally, accounting for approximately **19.41 million deaths annually**. Despite being a major global health crisis, many of these cases are preventable through early detection and lifestyle management.

This project, developed as part of the **DS512/513 Data Analytics** course, focuses on analyzing the **Framingham Heart Study dataset**. Instead of solely relying on prediction, our primary goal is to derive actionable intelligence by identifying concrete **"Risk Indicators"**.

### 🎯 Project Objectives

The analysis aims to answer critical questions regarding heart disease risk factors through statistical analysis and visualization:

* **Analyze Risk Factors:** Identify key drivers of Coronary Heart Disease (CHD) risk, including demographic (Age, Gender), behavioral (Smoking), and clinical factors (Glucose, BMI, Blood Pressure).
* **Visualize Insights:** Create interactive visualizations to clearly communicate risk patterns, such as the correlation between Glucose levels and Blood Pressure.
* **Develop Guidelines:** Use data-driven insights to propose preventive guidelines that promote healthier lifestyle behaviors.
* **Predictive Modeling (Secondary):** Develop a machine learning model to estimate 10-year CHD risk using techniques to handle class imbalance.

---

## 📂 Data Description

The dataset used in this analysis is the **Framingham Heart Study** dataset, obtained from Kaggle. It includes health records of residents from Framingham, Massachusetts, consisting of **4,238 records** and **15 attributes**.

* **Source:** [Kaggle - Heart Disease Prediction Using Logistic Regression](https://www.kaggle.com/datasets/dileep070/heart-disease-prediction-using-logistic-regression/data)
* **Target Variable:** `TenYearCHD` (10-year risk of coronary heart disease)
    * `0` = No Risk
    * `1` = Risk

### 📝 Data Dictionary

The variables are categorized into four main groups:

| Category | Variable Name | Description |
| :--- | :--- | :--- |
| **Target** | `TenYearCHD` | 10-year risk of coronary heart disease (Binary: 0/1) |
| **Demographic** | `male` | Gender (0 = Female, 1 = Male) |
| | `age` | Age of the patient |
| | `education` | Education level |
| **Behavioral** | `currentSmoker` | Whether the patient is a current smoker (0/1) |
| | `cigsPerDay` | Number of cigarettes smoked per day |
| **Medical History** | `BPMeds` | Whether the patient is on blood pressure medication |
| | `prevalentStroke` | History of stroke |
| | `prevalentHyp` | History of hypertension |
| | `diabetes` | History of diabetes |
| **Current Health** | `totChol` | Total cholesterol level |
| | `sysBP` | Systolic blood pressure |
| | `diaBP` | Diastolic blood pressure |
| | `BMI` | Body Mass Index |
| | `heartRate` | Heart rate |
| | `glucose` | Glucose level |

---

## 🧹 Data Cleaning & Preprocessing

To ensure the accuracy of our analysis and model, the following preprocessing steps were performed:

1.  **Data Integration & Mapping:**
    * Converted numerical codes into human-readable labels for analysis (e.g., mapping `Sex` to Male/Female, `TenYearCHD` to Risk/No Risk).
2.  **Handling Missing Values:**
    * Identified missing values (NaNs) in the dataset and removed the corresponding rows to maintain data integrity.

---

### 🚩 Problems Identified
Three critical data quality issues were identified during the exploration phase that required preprocessing:

1.  **Missing Values:** Several records contained null values that needed to be dropped or imputed.
2.  **Extreme Outliers:** Significant outliers were observed in medical variables, which could skew the analysis.
3.  **Imbalanced Target:** The dataset shows a class imbalance, with significantly fewer "Risk" cases compared to "No Risk" cases.

---

## ❓ Key Questions & Hypotheses

### 1. General Information
* **Age Impact:** Does age significantly impact the 10-year CHD risk?
* **Gender Differences:** Does the impact of age on CHD risk differ between genders?

### 2. Medical Data Factors
* **Dominant Factor:** Which is the dominant risk factor: Glucose or Cholesterol?
* **Glucose & BP:** Is elevated blood glucose associated with hig
her systolic blood pressure?
* **BMI Trend:** Does the BMI category (Underweight to Obese) show a clear trend in CHD risk?
* **Combined Risks:** Does having multiple risk factors increase the risk compared to just one?

---

## 📊 Findings & Insights: Age Impact on CHD Risk

### ❓ Key Question  
**Does age have a significant impact on ten-year CHD risk?**

### 🧠 Insight Summary  
**Consistent Age Impact:**  
Across both genders, individuals in the **Risk** group are consistently older than those in the **No Risk** group.  
This indicates that **age is a meaningful factor** contributing to the likelihood of developing ten-year CHD risk.

### 📈 Average Age by CHD Risk Group

| **CHD Risk Group** | **Average Age** |
|--------------------|-----------------|
| No Risk            | 49              |
| Risk               | 54              |
<img width="1019" height="287" alt="image" src="https://github.com/user-attachments/assets/f01442e2-17e0-4f90-af7a-81256deb4ff0" />

### 📝 Interpretation  
- **Age shows a direct and notable correlation** with CHD risk.  
- Individuals categorized as **Risk** tend to be **older on average**.  
- These findings support the importance of **age-targeted risk assessments** and **early prevention strategies**.

---

## 📊 Findings & Insights: Gender vs Age Impact on CHD Risk

### ❓ Key Question  
**Age is a risk factor — but is the impact of age on ten-year CHD risk different between genders?**

### 🧠 Insight Summary  
**Gender shows minimal impact** on heart disease risk,  
whereas **age proves to be the dominant factor** for both males and females.

### 📈 Average Age by CHD Risk Group & Gender

| **Gender** | **CHD Risk Group** | **Average Age** |
|------------|---------------------|------------------|
| Female     | Risk                | 55               |
| Female     | No Risk             | 49               |
| Male       | Risk                | 54               |
| Male       | No Risk             | 48               |

<img width="955" height="638" alt="image" src="https://github.com/user-attachments/assets/4252b5c4-d04c-41ea-9468-897bf968a8f9" />


### 📝 Interpretation  
- Differences between males and females are **small**, indicating gender does not strongly influence CHD risk.  
- In both genders, the **Risk** group is older than the **No Risk** group.  
- This reinforces that **age is the primary contributing factor**, regardless of gender.

---

## 📊 Findings & Insights: Glucose vs Cholesterol as Risk Factors

### ❓ Key Question  
**Which is the dominant risk factor: glucose or cholesterol?**

### 🧠 Insight Summary  
**High glucose is identified as the dominant risk factor,**  
significantly outweighing the impact of high cholesterol.

### 📈 CHD Risk Count by Glucose–Cholesterol Cluster

| **Glucose–Cholesterol Cluster** | **CHD Risk Group** | **Count** |
|---------------------------------|---------------------|-----------|
| High glucose                    | No Risk             | 20        |
| High glucose                    | Risk                | 20        |
| Low glucose, high cholesterol   | No Risk             | 501       |
| Low glucose, high cholesterol   | Risk                | 116       |
| Low glucose, low cholesterol    | No Risk             | 1,153     |
| Low glucose, low cholesterol    | Risk                | 158       |
| Low glucose, medium cholesterol | No Risk             | 1,425     |
| Low glucose, medium cholesterol | Risk                | 263       |

<img width="963" height="649" alt="image" src="https://github.com/user-attachments/assets/1e9bf92e-58f6-4572-b088-3e93be1d2142" />

### 📝 Interpretation  
- The **high glucose** group shows a **proportionally higher CHD risk**, even though the total sample size is smaller.  
- Clusters with **low glucose** have much larger populations but lower proportional CHD risk.  
- This highlights **glucose level as a stronger predictor** of CHD risk than cholesterol.

---

## 📊 Findings & Insights: Blood Glucose vs Systolic Blood Pressure (sysBP)

### ❓ Key Question  
**Is elevated blood glucose associated with higher systolic blood pressure (sysBP)?**

### 🧠 Insight Summary  
Elevated blood glucose is associated with **higher systolic blood pressure**, averaging **141.4 mmHg** compared to **131.6 mmHg** in the normal glucose group.  
This confirms a link between **high glucose levels and increased cardiovascular stress**.

### 📈 Average Systolic Blood Pressure by Glucose Group

| **Glucose Group** | **Avg. Systolic BP (mmHg)** |
|-------------------|------------------------------|
| High Glucose      | 141.405                      |
| Normal Glucose    | 131.586                      |
<img width="331" height="616" alt="image" src="https://github.com/user-attachments/assets/0e8f72d0-153e-4998-a5da-d87ea9ac55e0" />

### 📝 Interpretation  
- Individuals with **high glucose levels** exhibit **notably higher systolic blood pressure**.  
- Elevated systolic pressure is a known contributor to cardiovascular disease risk.  
- These findings strengthen the association between **glucose dysregulation** and **cardiovascular strain**.

---

## 📊 Findings & Insights: BMI Category and Ten-Year CHD Risk

### ❓ Key Question  
**Does the BMI category show a clear trend in Ten-Year CHD risk?**

### 🧠 Insight Summary  
**Heart disease risk rises with BMI**, peaking at nearly **20%** in the obese group  
compared to **12%** in normal-weight individuals.  
This confirms a strong association between **higher BMI and increased CHD risk**.

### 📈 Average Ten-Year CHD Risk by BMI Category

| **BMI Category**  | **Avg. Ten-Year CHD Risk** |
|-------------------|----------------------------|
| Normal weight     | 0.12022                    |
| Underweight       | 0.14286                    |
| Overweight        | 0.17309                    |
| Obese             | 0.19824                    |
<img width="425" height="623" alt="image" src="https://github.com/user-attachments/assets/bae3b670-50ce-40b1-829a-e5fe36b479b4" />


### 📝 Interpretation  
- There is a **clear upward trend**: CHD risk increases as BMI rises.  
- Obese individuals show the **highest estimated ten-year risk**, nearly **double** some lower BMI groups.  
- BMI therefore serves as a **strong predictive factor** for coronary heart disease.

---


## 💡 Conclusion of Findings and Insights

Based on our statistical analysis and data visualization, we identified several critical patterns regarding heart disease risk:

### 1. Demographic Factors: Age vs. Gender
* **Age is the Dominant Driver:** Age has a significant and consistent impact on CHD risk across all groups. The "Risk" group is consistently older than the "No Risk" group.
* **Gender Impact is Minimal:** Unlike age, gender shows minimal impact on heart disease risk. Age proves to be the primary determinant for both men and women.

### 2. Medical Risk Factors
* **Glucose vs. Cholesterol:** High glucose levels were identified as a dominant risk factor, significantly outweighing the impact of high cholesterol.
* **The Glucose-BP Connection:** Elevated blood glucose is strongly associated with higher systolic blood pressure (approx. 141 mmHg vs. 131 mmHg), confirming a link to increased cardiovascular stress.
* **BMI Trends:** There is a clear upward trend in risk associated with BMI. The 10-year CHD risk peaks at nearly **20% for the Obese group**, compared to approximately **12% for those with normal weight**.

