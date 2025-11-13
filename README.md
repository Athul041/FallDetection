# Fall Detection from PITCH Dataset
This project focuses on prognostic fall detection using data collected through the PITCH (Proactive, Integrated, Technology-enabled, patient-Centric, Home support) program — a collaboration between Kindred Home Care, the University of New Brunswick (UNB), and VeroSource Solutions.

The goal is to identify naturally forming clusters and predictive health indicators that can help forecast the likelihood of falls among older adults. The study builds upon prior exploratory analytics and machine learning work, expanding it through clustering and feature analysis.

---
## Dataset

Data was collected from in-home health assessments performed by Kindred caregivers through the PITCH program.

### Content
Each record represents a client’s health assessment, including:
- Demographics (age, gender, etc.)
- Physical indicators (heart rate, blood pressure, 4-meter walk test performance, BMI)
- Cognitive and mental health metrics (Mini-COG, SF-36)
- Health indicators (mobility, grooming, errands, home maintenance)
- Notable events (falls, hospitalizations, illnesses, health decline)

### Dimensions
- Patients: 315  
- Total records (after preprocessing): 419  
- Initial features: 149  
- Final processed features: 105  

---

## Methods

### 1. Data Preprocessing
- Converted categorical features using `pandas.factorize()`.
- Removed highly correlated features (|correlation| ≥ 0.9).
- Consolidated sparse and noisy features.
- Scaled features using `MinMaxScaler` (range 0–1).
- Normalized feature distributions to reduce skew and noise.

### 2. Clustering (Unsupervised Learning)
- Algorithm: K-Means (`lloyd` algorithm, Euclidean distance).
- Initialization: `kmeans++`.
- Optimal clusters (k) determined using the Elbow Method.
- Visualization: Principal Component Analysis (PCA) for 2D scatter plots.

### 3. Cluster Evaluation
- Internal metric: Sum of Squared Error (SSE).
- Visualization methods:
  - Correlation heatmap.
  - Histograms for feature distributions.
  - Scatter plots for clusters.
  - Parallel plots for cluster centroids.

---

## Experiments

| Stage | Technique | Purpose |
|--------|------------|----------|
| Correlation Analysis | Identify redundant or noisy features | Reduce feature dimensionality |
| Outlier Detection | Z-score based filtering | Improve K-Means performance |
| PCA | Dimensionality reduction | Visualize cluster separability |
| Decision Trees | Rule extraction | Identify dominant predictors |
| Sampling | Uniform class distribution | Balance target classes |

---

## Results

- Optimal number of clusters (k): 5 (identified via the Elbow Method).
- Most features were uncorrelated, indicating good potential for classification tasks.
- Distinct clusters identified, with some correlation to notable health events.
- Previous falls emerged as the strongest predictor of future falls.
- Survey-based features (numeric) produced better clustering results than categorical health indicators.


