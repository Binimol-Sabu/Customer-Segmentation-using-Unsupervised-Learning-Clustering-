# Customer-Segmentation-using-Unsupervised-Learning-Clustering


This project applies **unsupervised learning techniques** to segment wholesale customers based on their annual spending in various product categories. The objective is to discover hidden patterns that can support business decisions in **marketing**, **inventory management**, and **customer targeting**.

---

## 📂 Dataset Overview

- **Source**: Kaggle – Wholesale customers data
- **Attributes**:
  - `Fresh`, `Milk`, `Grocery`, `Frozen`, `Detergents_Paper`, `Delicassen` – Annual spending in monetary units (m.u.)
  - `Channel` – Type of customer (1: Horeca, 2: Retail)
  - `Region` – Geographical region (1: Lisbon, 2: Oporto, 3: Other)

---

## 🧼 Data Preprocessing

- Removed `Channel` and `Region` as they are not useful for unsupervised clustering.
- Checked and confirmed **no missing values** and **no duplicates**.
- Detected **high variance** and **outliers** in features.
- Dropped highly correlated feature (`Grocery`) based on the correlation matrix.

---

## 📊 Exploratory Data Analysis (EDA)

- **Boxplots and Histograms** used to detect skewness and outliers.
- **Correlation Heatmap** revealed strong correlation among `Milk`, `Grocery`, and `Detergents_Paper`.

---

## 📌 Clustering Techniques Applied

### 1️⃣ KMeans Clustering

- Applied **KMeans** with cluster range 2–10.
- Used **Elbow Method** to determine optimal `k` (inertia vs. clusters).
- Used **Silhouette Score** and **Davies-Bouldin Index** for evaluation.

| Clusters | Silhouette Score | Davies-Bouldin Index |
|----------|------------------|-----------------------|
| k = 4    | **0.398**        | **0.901**             |
| k = 5    | 0.378            | 0.915                 |
| k = 6    | 0.355            | —                     |

- **Best KMeans clustering at k = 4** based on evaluation metrics.

---

### 2️⃣ Hierarchical Clustering

- Used **Agglomerative Clustering** with `ward` linkage.
- Created **dendrogram** to visualize merge distances.
- Evaluated cluster quality for `n = 2` and `n = 4`.

| Clusters | Silhouette Score | Davies-Bouldin Index |
|----------|------------------|-----------------------|
| n = 2    | **0.558**        | **0.965**             |
| n = 3   | 0.308            | 1.010                 |

- **Best performance with 2 clusters** using hierarchical method.

---

## 📉 Dimensionality Reduction with PCA

- Applied **Principal Component Analysis (PCA)** to reduce features to 2 dimensions.
- Visualized clusters using **interactive Plotly scatter plots**.
- 
-  3️⃣ DBSCAN (Density-Based Spatial Clustering)

- Applied **DBSCAN** to detect arbitrary-shaped clusters and noise
- Tuned `eps` and `min_samples` using k-distance plot
- **Result**:
  - Returned **only one cluster**
  - DBSCAN failed to identify meaningful groupings in this dataset

> **Insight**: DBSCAN is not suitable for this dataset due to lack of dense region separation or structure. This highlights the importance of evaluating multiple methods.


---

## ✅ Conclusion

- **Hierarchical Clustering with 2 clusters** yielded the best results:
  - Highest **Silhouette Score**: `0.5583`
  - Lowest **Davies-Bouldin Index**: `0.9654`
- KMeans also performed reasonably well at `k=4`, but hierarchical clustering showed more distinct clusters.
- PCA and correlation analysis enhanced cluster interpretability and visualization.

---

## 🛠️ Tools & Libraries

- Python (Pandas, NumPy, Matplotlib, Seaborn)
- Scikit-learn
- SciPy
- Plotly


## 📁 Repository Structure

