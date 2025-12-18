# 🛍️ Customer Segmentation: Unsupervised Learning with K-Means

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Project Overview
This project tackles a classic **Unsupervised Learning** problem: grouping customers based on their demographics and spending behavior without pre-existing labels.

Using a real-world dataset (Split into Train/Test), I implemented **K-Means Clustering** to identify distinct customer profiles. A unique feature of this project is the **"Reality Check"** phase, where I compared my unsupervised mathematical clusters against actual ground-truth labels to validate the model's logic.

---

## 🛠 The Challenge: Split Datasets
Unlike simple tutorials, this dataset was split into `Train.csv` and `Test.csv`.
* **Problem:** If you Label Encode them separately, "Doctor" might be `0` in Train but `1` in Test, destroying data integrity.
* **Solution:** I implemented a **Combined Preprocessing Pipeline** to concatenate data, clean/encode uniformly, and then split it back for analysis.

---

## 🧹 Data Preprocessing & Feature Engineering
* **Missing Value Imputation:**
    * *Categorical (e.g., Profession):* Filled with **Mode** (Most Frequent).
    * *Numerical (e.g., Family Size):* Filled with **Median** to avoid outlier skew.
* **Encoding Strategy:**
    * **Ordinal Encoding:** Applied to `Spending_Score` (Low < Average < High) to preserve rank.
    * **Label Encoding:** Applied to nominal features like `Gender` and `Profession`.
* **Scaling:** Applied `StandardScaler` to normalize features (e.g., Age vs Income) so K-Means calculates distances accurately.

---

## 📉 Methodology: Finding the "K"
I used the **Elbow Method** to determine the optimal number of clusters.
* The metric **WCSS (Within-Cluster Sum of Squares)** drops significantly as clusters increase.
* The "Elbow" (bend) appeared clearly at **K=4**, indicating four distinct customer segments.

*(Note: Upload your Elbow Plot here)*
![Elbow Method Plot](images/elbow_plot.png)

---

## 📊 Results: The Reality Check
After assigning customers to Clusters 0-3, I validated the results against the `Segmentation` column in the training set using a Confusion Matrix Heatmap.

**Key Insight:**
* **Cluster 2** showed a massive overlap with **Segment D**.
* This proves the algorithm successfully identified the "Segment D" demographic (typically younger, healthcare-focused) purely through mathematical patterns, without ever seeing the labels.

*(Note: Upload your Heatmap here)*
![Confusion Matrix Heatmap](images/heatmap_plot.png)

---

## 🚀 How to Run
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/customer-segmentation.git](https://github.com/your-username/customer-segmentation.git)
