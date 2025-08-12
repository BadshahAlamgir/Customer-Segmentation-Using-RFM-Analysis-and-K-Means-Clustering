# Customer Segmentation Using RFM Analysis and K-Means Clustering

## Project Overview

This project performs customer segmentation on transactional sales data using the classic **RFM (Recency, Frequency, Monetary)** model combined with **K-Means clustering**. The goal is to identify distinct customer groups based on purchasing behavior to enable targeted marketing, personalized communication, and improved customer retention strategies.

The dataset includes transactional details such as invoice numbers, product codes and descriptions, quantities, unit prices, invoice dates, customer IDs, and countries.

---

## Dataset

The data contains the following key fields:

- **InvoiceNo:** Unique invoice number per transaction.
- **StockCode:** Product identifier.
- **Description:** Product description.
- **Quantity:** Number of units purchased.
- **InvoiceDate:** Date and time of transaction.
- **UnitPrice:** Price per unit.
- **CustomerID:** Unique identifier for each customer.
- **Country:** Customer’s country.

Canceled transactions and entries missing customer IDs are removed during preprocessing.

---

## Methodology

This project follows a structured approach combining data cleaning, feature engineering, transformation, clustering, and visualization:

- **Data Cleaning:** Canceled transactions (invoice numbers starting with 'C') and transactions with missing `CustomerID` or non-positive quantities are removed to ensure data quality.

- **Feature Engineering:** For each customer, the following metrics are calculated:  
  - *Recency*: Days since the last purchase relative to the dataset’s most recent transaction date.  
  - *Frequency*: Number of unique purchase occasions.  
  - *Monetary*: Total amount spent.

- **Data Transformation:** To handle skewed distributions, Frequency and Monetary values undergo log transformation (`log(1 + x)`). All RFM features are then standardized using z-score scaling to ensure balanced influence during clustering.

- **Clustering:**  
  - The **K-Means** algorithm partitions customers into clusters by iteratively assigning customers to the nearest cluster centroid and updating centroids to minimize the Within-Cluster Sum of Squares (WCSS).  
  - The optimal number of clusters is selected using the Elbow Method, which plots WCSS for different cluster counts and identifies the point where gains plateau.

- **Visualization:** Multiple visualizations are created to analyze and present the segments:

  1. **Histograms:** Show distributions of Recency, Frequency, and Monetary metrics, helping to understand data skewness and spread.

  2. **Radar Charts:** Profile each cluster by displaying normalized average RFM values in a circular radar plot, highlighting the behavioral differences among segments.

  3. **Interactive 3D Scatter Plot:** Visualizes customers in three-dimensional space (Recency, Frequency, Monetary) with colors representing cluster membership, allowing rotation, zooming, and detailed exploration.

---
## Visualizations

The project produces the following key visualizations to explore and present customer segments:

### 1. Distribution Histograms of RFM Metrics  
These histograms show how Recency, Frequency, and Monetary values are distributed across all customers.  
- **Recency:** Helps identify how recent most purchases are and detect inactive customers.  
- **Frequency:** Reveals how often customers make purchases, highlighting loyal vs occasional buyers.  
- **Monetary:** Displays spending patterns, distinguishing high spenders from low spenders.

Example (Recency Distribution):  
![Recency Histogram](path/to/recency_histogram.png) *(Replace with actual screenshot)*

---

### 2. Radar Charts of Cluster Profiles  
For each customer segment, a radar chart plots the normalized average Recency, Frequency, and Monetary values on a circular graph. This visually contrasts customer groups, showing which segments have higher loyalty, spending, or inactivity.

Example Radar Chart for Cluster 0:  
![Radar Chart Cluster 0](path/to/radar_cluster0.png)

---

### 3. Interactive 3D Scatter Plot of Customer Segments  
An interactive Plotly 3D scatter plot visualizes customers in three dimensions—Recency, Frequency, and Monetary—with color-coded clusters. Users can rotate and zoom to explore clusters’ separations and overlaps, gaining deeper insight into segment characteristics.

Interactive plot example (view live or open saved HTML):  
![3D Scatter Plot](path/to/3d_scatter_placeholder.png)

*To view the interactive plot, open `customer_segmentation_3d.html` in a web browser.*

---
## Tools & Libraries

- Python 3.x  
- Pandas, NumPy for data manipulation  
- Matplotlib, Seaborn for static visualizations  
- Scikit-learn for clustering and preprocessing  
- Plotly for interactive 3D visualization

---

## How to Run

1. Clone the repository.  
2. Install required packages:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn plotly
