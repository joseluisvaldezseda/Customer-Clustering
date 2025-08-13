# VFR Analysis with Robust Clustering

This project implements a **robust clustering algorithm** to segment customers based on **VFR metrics (Sales, Frequency, Recency)**, optimizing memory usage, removing outliers, and evaluating multiple clustering models.

## Objective
Classify customers into homogeneous groups according to their purchasing behavior, supporting data-driven business and marketing strategies.

## Methodology

1. **Data Loading and Preparation**
   - Only the necessary columns are read from a CSV file.
   - Data types are converted to optimize memory usage.
   - *Recency (days)* is calculated from the last purchase date.
   - Invalid data is filtered out (sales and frequencies <= 0).
   - Outliers are removed using the 99th percentile.
   - Recency is limited to a maximum of 366 days.

2. **Variable Standardization**
   - Scaling with `StandardScaler` ensures all metrics have equal weight in the clustering process.

3. **Clustering**
   - Models tested:
     - **KMeans**
     - **MiniBatchKMeans**
     - **Birch**
   - **Silhouette Score** is used to evaluate cluster cohesion and separation.
   - Different *k* values are compared to find the best segmentation.

4. **Model Evaluation and Selection**
   - The model with the highest silhouette score is chosen.
   - A final DataFrame is generated with the cluster assigned to each customer.

5. **Results Export**
   - Results and metrics are exported to CSV for further analysis.

## 📊 Metrics Used
- **Total Sales Amount**: Total amount purchased by the customer.
- **Transaction Count**: Number of transactions made.
- **Recency (days)**: Days since the last purchase.

## Main Libraries
- `pandas`
- `numpy`
- `scikit-learn`
- `tqdm`

## Execution
1. Place the historical data CSV file in the project folder.
2. Run the script or notebook.
3. Review the output file with the generated clusters.

---

This pipeline ensures a more robust clustering thanks to:
- Strict data filtering.
- Removal of extreme outliers.
- Comparison of multiple clustering algorithms.
