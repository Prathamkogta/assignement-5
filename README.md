# DA5401 Assignment 5: Visualizing Data Veracity Challenges in Multi-Label Classification

This notebook implements **t-SNE** and **Isomap** visualization techniques to identify data quality issues in the **Yeast multi-label classification dataset**.

---

## 📌 Assignment Overview

The **Yeast dataset** contains gene expression data with:
- **2417 instances**
- **103 features**
- **14 functional class labels**

### Goals:
- Use **dimensionality reduction** techniques to visually identify:
  - **Noisy/Ambiguous Labels**
  - **Outliers**
  - **Hard-to-Learn Samples**

---

## 🗂 Dataset

- **Source**: UCI Yeast Dataset (via `fetch_openml`)
- **Features**: 103 numerical gene expression features
- **Labels**: 14 multi-label functional classes
- **Preprocessing**:
  - StandardScaler applied for feature normalization
  - Multi-label target converted to binary matrix

---

## 🛠 Techniques Used

### 1. **t-SNE (t-Distributed Stochastic Neighbor Embedding)**
- Non-linear dimensionality reduction
- Preserves local neighborhood structure
- **Perplexity values tested**: 5, 30, 50

### 2. **Isomap (Isometric Mapping)**
- Non-linear technique preserving geodesic distances
- **Neighbors parameter**: 5, 10, 15

---

## 📊 Visualization Approach

### Label Simplification:
To make visualizations interpretable, labels are simplified into:
1. **Two most frequent single-label classes**
2. **Most frequent multi-label combination**
3. **"Other" category** for remaining instances

### Color Coding:
- Each category is assigned a unique color using `plt.cm.Set1`
- Interactive legends show category distributions

---

## 🔍 Key Findings

### Data Quality Issues Identified:
- **Label Imbalance**: Some labels appear in <2% of instances
- **Cluster Overlap**: Suggests ambiguous or noisy labeling
- **Outliers**: Isolated points indicating potential data errors
- **Hard-to-Learn Samples**: Points in mixed-label regions

### Optimal Parameters:
- **t-SNE**: Perplexity=30 provided best separation
- **Isomap**: n_neighbors=15 captured meaningful structure

---

## 📈 Results

- **t-SNE**: Better at separating distinct label groups
- **Isomap**: Preserved global structure but showed more overlap
- **Both techniques** revealed similar outlier patterns
- **Label ambiguity** visually confirmed through overlapping clusters

---

## 🚀 How to Use

### Prerequisites:
```python
pip install scikit-learn matplotlib seaborn pandas numpy scipy
