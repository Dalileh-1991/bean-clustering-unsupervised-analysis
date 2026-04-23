# Dry Bean Dataset — Unsupervised Learning Project

## Project Overview

This project explores the **Dry Bean Dataset** using several unsupervised learning methods to discover hidden structure in bean samples based on their geometric and shape-related features.

The main goal is to evaluate whether unsupervised models can recover meaningful groupings that are close to the **7 known bean classes**.

The project applies:

- Exploratory Data Analysis
- Feature scaling
- Principal Component Analysis
- KMeans Clustering
- Gaussian Mixture Models
- Agglomerative Clustering
- DBSCAN
- Kernel PCA + KMeans
- Internal and external clustering evaluation metrics

---

## Dataset

The dataset used in this project is the **Dry Bean Dataset** from the UCI Machine Learning Repository.

It contains measurements extracted from images of dry beans.  
The target labels represent 7 bean varieties:

- SEKER
- BARBUNYA
- BOMBAY
- CALI
- DERMASON
- HOROZ
- SIRA

Although this is an unsupervised learning project, the true labels are used only for external evaluation.

---

## Project Objective

The objective of this project is to identify meaningful natural groupings in the Dry Bean Dataset and compare how well different clustering models capture the underlying class structure.

The analysis focuses on two main questions:

1. Which models produce well-separated clusters?
2. Which models best recover the known 7 bean classes?

---

## Methods Used

### Data Preprocessing

The numerical features were scaled before applying clustering models.  
Scaling is important because clustering algorithms are distance-based and can be strongly affected by feature magnitude.

### Dimensionality Reduction

Principal Component Analysis was used to reduce feature redundancy and simplify the feature space.

The PCA results showed that:

- 2 components explain about 81.9% of the variance
- 3 components explain about 89.9% of the variance
- 5 components explain about 97.8% of the variance
- 8 components explain about 99.93% of the variance

This confirms that PCA is highly suitable for this dataset.

### Clustering Models

The following models were tested:

- KMeans
- Gaussian Mixture Models
- Agglomerative Clustering
- DBSCAN
- PCA + KMeans
- PCA + Gaussian Mixture
- PCA + Agglomerative Clustering
- PCA + DBSCAN
- Kernel PCA + KMeans

---

## Evaluation Metrics

The models were evaluated using both internal and external clustering metrics.

### Internal Metric

- Silhouette Score

This measures how well-separated and compact the clusters are.

### External Metrics

Because the dataset has known class labels, external metrics were also used:

- Adjusted Rand Index
- Normalized Mutual Information
- Homogeneity
- Completeness
- V-measure

These metrics compare the cluster assignments with the true bean classes.

---

## Key Finding

A major finding of this project is that **silhouette score alone can be misleading**.

Some models produced high silhouette scores but found only 2 or 3 clusters.  
These clusters were geometrically well separated, but they did not match the real 7 bean classes well.

Therefore, external metrics such as ARI, NMI, and V-measure were more useful for final model selection.

---

## Final Model

The best final model was:

**PCA + Gaussian Mixture Model**

with:

- 2 principal components
- 7 Gaussian mixture components
- full covariance

This model achieved the strongest agreement with the true bean classes.

Approximate results:

- ARI: 0.722
- NMI: 0.758
- V-measure: 0.758

This made it the most meaningful model for recovering the real class structure of the dataset.

---

## Interpretation

The final clustering result showed that the model was able to recover much of the real class structure.

Some classes, such as BOMBAY, were clearly separated.  
Other classes, such as BARBUNYA and CALI, showed more overlap because their geometric features are naturally similar.

This suggests that unsupervised learning can reveal meaningful structure in the Dry Bean Dataset, but some bean varieties are harder to separate without supervision.

---

## Limitations

This project has some limitations:

- Some bean classes overlap naturally
- Clustering models do not guarantee exact recovery of real labels
- Results depend on hyperparameter choices
- Duplicate observations may affect clustering structure
- PCA may remove some nonlinear information

---

## Future Work

Possible future improvements include:

- Removing duplicate observations before modeling
- Performing deeper hyperparameter tuning
- Testing additional nonlinear dimensionality reduction methods
- Comparing results with supervised classification models
- Investigating class-level overlap in more detail

---

## Conclusion

This project shows that the Dry Bean Dataset contains meaningful structure that can be discovered through unsupervised learning.

The analysis also demonstrates that choosing a clustering model should not depend on silhouette score alone.  
For this dataset, the most useful model was the one that best recovered the known 7 bean classes.

Overall, **PCA + Gaussian Mixture Model** provided the strongest and most meaningful final clustering solution.
