# 🍔 Fast Food Nutrition Analysis & Clustering

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Project Overview
This project analyzes the nutritional content of menu items from major US fast-food chains (McDonald's, Taco Bell, Chick-Fil-A, etc.). The goal is to identify healthy options using a custom "Health Score" and to segment menu items into distinct categories using Unsupervised Machine Learning (K-Means Clustering).

This analysis is part of the **Business Analytics** course project.

## 📂 Dataset
The dataset (`fastfood.csv`) contains nutritional information for 515 menu items across various restaurants.
* **Source:** [Fast Food Nutrition Dataset] (Kaggle/Open Source)
* **Key Features:** Calories, Total Fat, Sodium, Sugar, Protein, Fiber, and Vitamins.
* **Restaurants Included:** McDonald's, Burger King, Taco Bell, Chick-Fil-A, Sonic, Arby's, Dairy Queen, Subway.

## 🧪 Hypotheses
1.  **Macro Correlation:** Total Fat is the primary driver of high caloric content in fast food, more so than sugar or protein.
2.  **Menu Segmentation:** Menu items can be automatically grouped into distinct dietary categories (e.g., "Diet-Friendly" vs. "Indulgence") based on their nutritional profile without manual labeling.

## ⚙️ Methodology & Workflow

### 1. Data Cleaning
* Handled missing values in `fiber`, `protein`, and vitamins by assuming 0 for null entries.
* **Quality Control:** Identified and removed erroneous data. specifically the *"Sonic Ultimate Chicken Club"* (Row 127), which listed 100 calories for a 64g fat item (mathematically impossible).

### 2. Exploratory Data Analysis (EDA)
* **Distribution Analysis:** Used Boxplots to compare calorie and sodium ranges across different restaurants.
* **Correlation Heatmap:** Confirmed a very strong correlation ($0.96$) between Calories and Total Fat.

### 3. Feature Engineering: Health Score
Created a custom metric (0-100 scale) to rank menu items:
* **Negative Factors (Lower is better):** Calories, Total Fat, Sodium, Sugar (60% weight).
* **Positive Factors (Higher is better):** Protein, Fiber (40% weight).
* *Result:* Chick-Fil-A and Subway dominated the Top 10 healthiest items list.

### 4. Machine Learning: K-Means Clustering
Applied K-Means algorithm to segment the menu items into 3 clusters based on `calories`, `total_fat`, `sugar`, and `protein`.

* **Preprocessing:** Used `StandardScaler` to normalize data (Z-Score).
* **Optimal K:** Determined $k=3$ using the Elbow Method and Silhouette Score (~0.38).

## 📊 Results: Cluster Interpretation

| Cluster | Label | Characteristics (Z-Score Analysis) |
| :--- | :--- | :--- |
| **0** | **Heavy / Indulgence** | Very high calories, fat, and sodium. Typically large burgers or combos. |
| **1** | **Light / Diet-Friendly** | Below-average calories and fat. Mostly salads, nuggets, or small items. |
| **2** | **Standard / Moderate** | Average nutritional values. Typical main menu items. |

## 🛠️ Technologies Used
* **Python**
* **Pandas & NumPy:** Data manipulation.
* **Matplotlib & Seaborn:** Data visualization.
* **Scikit-Learn:** Data preprocessing (MinMax/Standard Scaler) and K-Means Clustering.

## 🚀 How to Run
1.  Clone this repository.
2.  Install dependencies:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn
    ```
3.  Open `FastFood.ipynb` in Jupyter Notebook or Google Colab.
4.  Ensure `fastfood.csv` is in the same directory.
5.  Run all cells.

---
*Created by [Your Name / Team Name]*
