# 📊 Rossmann Store Sales Prediction using Linear Regression & XGBoost

## 📌 Overview
This project applies **Linear Regression** and **XGBoost** to predict daily sales for Rossmann drug stores. The dataset, sourced from Kaggle's "Rossmann Store Sales" competition, includes **historical sales data from 1,115 stores** across **multiple European countries**. The goal is to build predictive models that account for key influencing factors like promotions, holidays, seasonality, and competition.

## 📂 Contents
1. [Introduction](#-introduction)  
2. [Data Exploration & Cleaning](#-data-exploration--cleaning)  
3. [Feature Engineering](#-feature-engineering)  
4. [Modeling: Linear Regression & XGBoost](#-modeling-linear-regression--xgboost)  
5. [Evaluation & Results](#-evaluation--results)  
6. [Conclusion](#-conclusion)  
7. [How to Run the Project](#-how-to-run-the-project)  

---

## 📖 Introduction
Rossmann operates over **3,000 stores** across Europe. Accurately predicting daily sales is crucial for **inventory management, staffing, and business strategy**. 

✔ **Objective:** Build a predictive model to forecast **daily sales up to 6 weeks in advance**.  
✔ **Models Used:** **Linear Regression** (for baseline) & **XGBoost** (for better performance).  
✔ **Key Influencing Factors:** **Promotions, holidays, seasonality, store competition, and location.**  

---

## 🔍 Data Exploration & Cleaning
### **📊 Data Overview & Initial Observations**
- **Dataset contains sales data from 1,115 stores**.
- **Features include numerical (sales, customers, store ID, competition distance, etc.) and categorical (store type, promotions, holidays, etc.).**
- **Missing Values Identified:**
  
![image](https://github.com/user-attachments/assets/b3a68d0d-c770-4726-a7e3-01d9e120850e)

  - `CompetitionDistance`: Some missing values are due to new stores that are not competitive nearby.
  - `Promo2`: Missing values for stores that never participated in Promo2.
  - `Open`: Some missing values on holidays when stores were closed.

### **🧹 Handling Missing Data**
✔ **CompetitionDistance:** Missing values were filled with the **median competition distance** of other stores.  
✔ **Promo2:** Missing values were replaced with `0` (indicating the store never participated in Promo2).  
✔ **Open Column:** Missing values were filled with `0` (store was closed).  

### **📊 Data Visualization & Insights**
✔ **Sales Distribution:** Right-skewed distribution, with many stores having sales below the median.  
![image](https://github.com/user-attachments/assets/34f3a8a7-b26a-47da-9bf7-400baf30b461)

✔ **Feature Importance Analysis:**
![image](https://github.com/user-attachments/assets/0effec0f-0c6c-4e82-b18b-c7b93a780612)

  - **Promo is the most influential feature**, contributing the most to sales predictions.
  - **Store type, competition distance, and holidays also play key roles.**

---

## 🛠 Feature Engineering
Feature engineering was performed to enhance model performance:
✔ **Created New Features:**
   - `year`, `month`, `day_of_week` from date.
   - `is_promo_active`, `is_holiday`, `is_weekend` flags.
   - `competition_distance_log` for better distribution handling.
✔ **Encoded Categorical Variables:**
   - Used **one-hot encoding** for categorical variables (e.g., store type, holidays).
✔ **Handled Missing Values:**
   - Used mean imputation for numerical values and mode imputation for categorical values.

---

## 🤖 Modeling: Linear Regression & XGBoost
### **1️⃣ Linear Regression (Baseline Model)**
- **Pros:** Easy to interpret, fast to train.
- **Cons:** Assumes linearity and struggles with complex relationships.

### **2️⃣ XGBoost (Gradient Boosting Decision Trees)**
- **Pros:** Handles non-linearity, interactions, and missing values well.
- **Cons:** Computationally expensive, requires hyperparameter tuning.

✔ **Hyperparameter tuning was performed using GridSearchCV.**  
✔ **Data was split into 80% training and 20% testing sets.**

---

## 📊 Evaluation & Results
The models were evaluated using **RMSE (Root Mean Squared Error)** and **R² (Coefficient of Determination)**.

| Model               | RMSE  | R² Score |
|---------------------|-------|----------|
| Linear Regression  | 2864  | 0.72     |
| XGBoost           | **1743**  | **0.91**     |

✔ **XGBoost significantly outperforms Linear Regression** due to its ability to capture complex patterns.  
✔ The lower RMSE of XGBoost indicates **better prediction accuracy**.

---

## ✅ Conclusion
✔ **XGBoost is the best model** for predicting Rossmann sales, achieving a high **R² score of 0.91**.  
✔ **Key Features Impacting Sales:** Promotions, holidays, competition, and store type. Especially promotions, Stores  with active promotions had significantly higher sales.
✔ **Future Work:** Consider using **LSTM (for time series forecasting)** or **AutoML models** to further improve accuracy.

---

## 🚀 How to Run the Project
### **1️⃣ Clone the Repository**
```sh
 git clone https://github.com/machine-learning-project.git
```

### **2️⃣ Install Dependencies**
```sh
 pip install -r requirements.txt
```

### **3️⃣ Run the Jupyter Notebook**
```sh
 jupyter notebook SalesPrediction_LinearRegression&XGBoost.ipynb
```

---

## 👥 Contributors
- **Anh Doan**
- **Anh Dinh**
- **Duy Le**
- **Thao Chu**

📌 **Feel free to contribute, suggest improvements, or report issues!** 🚀
