# Consensus-Based Ensemble Clustering for Customer Segmentation

##  Project Overview

This project implements a **Consensus-Based Ensemble Clustering** framework for **customer segmentation** using multiple unsupervised learning algorithms. Instead of relying on a single clustering model, it combines the outputs of multiple clustering methods to generate a more stable and accurate final segmentation.

Traditional clustering algorithms such as **K-Means**, **Agglomerative Clustering**, and **DBSCAN** often produce different results depending on assumptions, initialization, or parameter settings. This project addresses that issue using **Ensemble Clustering (Consensus Clustering)**.

---

##  Objectives

- Apply multiple clustering algorithms to the same dataset  
- Compare individual clustering performance  
- Build a **Co-Association Matrix** from clustering outputs  
- Generate final consensus clusters  
- Visualize customer groups and evaluate cluster quality  

---

##  Dataset

Recommended dataset: **Mall Customers Dataset**

### Features:
- `CustomerID`
- `Gender`
- `Age`
- `Annual Income (k$)`
- `Spending Score (1-100)`

---

##  Tech Stack

- Python
- Jupyter Notebook
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- scipy

---

##  Methodology

### 1. Data Preprocessing
- Load CSV file using `pandas.read_csv()`
- Handle missing values
- Encode categorical features (`Gender`)
- Standardize numerical features using `StandardScaler`

### 2. Base Clustering Models
Applied the following algorithms:

- **K-Means**
- **Agglomerative Clustering**
- **DBSCAN**

Each model generates cluster labels for every customer.

### 3. Co-Association Matrix
For each pair of customers `(i, j)`:

- If clustered together → `1`
- Else → `0`

Average agreement across all clustering algorithms:

`CoAssociation(i,j) = Number of times grouped together / Total algorithms`

This matrix captures pairwise clustering stability.

### 4. Consensus Clustering
The co-association matrix is converted into a distance matrix and clustered using:

- **Agglomerative Clustering**

This produces the final ensemble clusters.

---

##  Evaluation Metrics

Used to compare individual models vs ensemble model:

- **Silhouette Score** (Higher is better)
- **Davies-Bouldin Index** (Lower is better)

---

##  Visualizations

- PCA-based 2D cluster scatter plots
- Heatmap of co-association matrix
- Before vs After clustering comparison
- Final ensemble cluster visualization

---

##  How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

Open the notebook:

```bash
jupyter notebook
```

Run:

`Ensemble_Clustering_Customer_Segmentation.ipynb`

Replace the dataset path inside:

```python
df = pd.read_csv("YOUR_FILE_PATH.csv")
```

---

##  Project Structure

```text
├── Ensemble_Clustering_Customer_Segmentation.ipynb
├── README.md
├── clustered_customers.csv
├── Mall_Customers.csv
```

---

##  Key Findings

- Different clustering algorithms produce different customer groups
- Consensus clustering improves robustness
- Ensemble method often gives better cluster separation
- Pairwise agreement helps create stable segmentation

---

##  Research Contribution

This project demonstrates:

- Multi-model clustering ensemble techniques
- Similarity learning through co-association matrices
- Comparative unsupervised learning analysis
- Practical customer analytics

---

##  Future Improvements

- Weighted ensemble clustering
- Automatic cluster number selection
- Larger e-commerce datasets
- Interactive dashboards using Streamlit / Power BI

---

##  Conclusion

**Summary of Findings:**

| Algorithm | Strength | Weakness |
|---|---|---|
| K-Means | Fast, scalable | Assumes spherical clusters |
| Agglomerative | Hierarchical structure | Slow on large data |
| DBSCAN | Finds arbitrary shapes, handles noise | Sensitive to `eps` |
| **Ensemble** | **Combines all advantages** | **More complex pipeline** |

**Key Insight — Co-Association Matrix:**
- Each cell `M[i,j]` records how consistently two customers are placed together across all algorithms.
- This acts as a **learned similarity** that is more robust than any single distance metric.
- Final Agglomerative Clustering on this matrix produces **stable, meaningful segments**.

**Conclusion:**  
Ensemble clustering improves the robustness and accuracy of customer segmentation by combining multiple clustering algorithms. The co-association matrix effectively captures pairwise relationships, resulting in more stable and meaningful clusters compared to individual methods — as evidenced by the improved **Silhouette Score** and lower **Davies-Bouldin Index**.

---
*Built with: scikit-learn · numpy · matplotlib · seaborn · scipy*
---

## 👤 Author

- Devashish Komiya  
- Sahasranshu Behera
- Nikhil Kumar 
- Ayush Raj 


