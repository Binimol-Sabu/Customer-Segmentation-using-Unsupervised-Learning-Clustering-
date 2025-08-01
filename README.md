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
- 🎯 K-Means with PCA
| Metric               | Score    | Interpretation          |
|----------------------|----------|-------------------------|
| Silhouette Score     | 0.586    | Excellent separation    |
| Davies-Bouldin Index | 0.809    | Compact cluster formation|
| Optimal Clusters     | 2        | Determined via elbow method |

**Key Steps**:
1. PCA reduced dimensions to 2 components (80% variance retained)
2. Standardized features before clustering
3. Visualized clear separation in 2D space

- 
-  3️⃣ DBSCAN (Density-Based Spatial Clustering)

- Applied **DBSCAN** to detect arbitrary-shaped clusters and noise
- Tuned `eps` and `min_samples` using k-distance plot
- **Result**:
  - Returned **only one cluster**
  - DBSCAN failed to identify meaningful groupings in this dataset

> **Insight**: DBSCAN is not suitable for this dataset due to lack of dense region separation or structure. This highlights the importance of evaluating multiple methods.



## ✅ Conclusion
    K-Means with PCA (Best Performer)
    Silhouette Score: 0.586 (Exceeds 0.5 threshold for meaningful structure)
    Davies-Bouldin: 0.809 (Closest to 0 = best separation)

## 🛠️ Tools & Libraries

- Python (Pandas, NumPy, Matplotlib, Seaborn)
- Scikit-learn
- SciPy
- Plotly




