## Wastewater Dataset Analysis

### Feature Correlations (Heatmap Insights)
- **Temperature metrics** (maximum, minimum, and average) are highly correlated — expected due to consistent weather patterns.
- **Chemical Oxygen Demand (COD)** is strongly correlated with both **Total Nitrogen** and **Biological Oxygen Demand (BOD)** — consistent with shared nutrient and organic matter loads.
- **Temperature** shows little correlation with nutrient-related features such as oxygen, ammonia, and nitrogen — suggesting microbial activity may be driven more by chemical composition than temperature in this dataset.

---

### Class Distribution
- ~460 samples indicate **medium microbial activity**
- ~510 samples indicate **high microbial activity**
- ~400 samples indicate **low microbial activity**

Note: The wastewater dataset was evenly distributed across the three classes (low, medium, and high microbial activity). As a result, the confusion matrices showed that misclassifications were equally likely to occur between adjacent classes. For example, actual medium samples were misclassified as high as often as they were misclassified as low.

The performance metrics and model evaluations reported reflect this balanced distribution, where the models performed with a more even tendency to mislabel each class, compared to an imbalanced dataset.

---

### PCA Feature Distributions (Histograms)
- All principal components used in analysis are **approximately normally distributed**, suggesting successful dimensionality reduction and feature scaling.

---

### Pair Plots for Feature Relationships
- **Ammonia** shows a **strong positive correlation** with both **BOD** and **COD**, reflecting its role in overall organic load.
- **Temperature metrics** show **little to no correlation** with chemical indicators like ammonia, nitrogen, and oxygen demand — reinforcing the idea that microbial activity may not be directly temperature-driven in this dataset.

---

## Confusion Matrices for Each Model

### Gaussian Naive Bayes
- **Correct Predictions:**
  - 88 medium, 88 high, 87 low
- **Incorrect Predictions:**
  - 2 medium predicted as high, 2 medium predicted as low
  - 5 high predicted as medium, 3 high predicted as low
  - 2 low predicted as high

### Logistic Regression
- **Correct Predictions:**
  - 90 medium, 95 high, 88 low
- **Incorrect Predictions:**
  - 2 medium predicted as high
  - 1 high predicted as low
  - 1 low predicted as high

### Decision Tree
- **Correct Predictions:**
  - 79 medium, 77 high, 82 low
- **Incorrect Predictions:**
  - 5 medium predicted as high, 8 medium predicted as low
  - 12 high predicted as medium, 7 high predicted as low
  - 4 low predicted as medium, 3 low predicted as high

### Support Vector Classifier (SVC)
- **Correct Predictions:**
  - 87 medium, 90 high, 88 low
- **Incorrect Predictions:**
  - 4 medium predicted as high, 1 medium predicted as low
  - 3 high predicted as medium, 3 high predicted as low
  - 1 low predicted as high

### K-Nearest Neighbors (KNN)
- **Correct Predictions:**
  - 84 medium, 88 high, 84 low
- **Incorrect Predictions:**
  - 5 medium predicted as high, 3 medium predicted as low
  - 3 high predicted as medium, 5 high predicted as low
  - 5 low predicted as high

--- 

## Classification Reports for Each Model

### Logistic Regression
- Accuracy: 98.5%
- Precision: 98.6%
- Recall: 98.6%
- F1-Score: 98.6%
- Cross Validation:
  - Accuracy: 97.5%
  - Standard Deviation: 0.02

### Support Vector Classifier (SVC)
- Accuracy: 95.6%
- Precision: 95.7%
- Recall: 95.7%
- F1-Score: 95.7%
- Cross Validation:
  - Accuracy: 95.3%
  - Standard Deviation: 0.03

### Gaussian Naive Bayes
- Accuracy: 94.9%
- Precision: 94.9%
- Recall: 95%
- F1-Score: 95%
- Cross Validation:
  - Accuracy: 94.6%
  - Standard Deviation: 0.02

### K-Nearest Neighbors (KNN)
- Accuracy: 92.4%
- Precision: 92.6%
- Recall: 92.5%
- F1-Score: 92.5%
- Cross Validation:
  - Accuracy: 93.9%
  - Standard Deviation: 0.03

### Decision Tree
- Accuracy: 85.9%
- Precision: 86.1%
- Recall: 86.1%
- F1-Score: 85.9%
- Cross Validation:
  - Accuracy: 87.7%
  - Standard Deviation: 0.03

### Discussion: Model Performance on the Wastewater Dataset

The wastewater dataset contained 1,382 entries, making it the larger of the two datasets analyzed. Among the five models tested, **Logistic Regression** consistently achieved the highest performance across all key metrics — including accuracy, precision, recall, and F1 score — both with and without cross-validation.

- **SVC** showed a 2.9% decrease across all metrics.
- **Gaussian Naive Bayes** was 3.6% lower across all metrics.
- **KNN** had a 6.1% decrease across all metrics.
- **Decision Tree** exhibited the largest drop, with a 12.1% reduction across all metrics.

--- 

## Wastewater Dataset

Data for this project was obtained from an inner join of open access data provided by Melbourne Water and the Melbourne Airport weather station. You can access the dataset [here](https://data.mendeley.com/datasets/pprkvz3vbd/1).

### Defining Microbial Activity Levels

Microbial activity in wastewater is defined based on biological process markers. Using clustering techniques, I labeled the data into three tiers of activity: **low**, **medium**, and **high**, based on previously observed patterns. The following metrics were used to determine these activity levels:

- **High Temperature, Low Ammonia/Nitrogen, and Low BOD** indicate higher microbial activity.
- **Low Temperature, High Ammonia/Nitrogen, and High BOD** are indicative of an environment less conducive to microbial activity.

### Key Metrics and Their Impact

- **High Temperature** indicates increased microbial activity. Microbial metabolism increases with temperature. Most wastewater microbes are mesophiles, which are most active between 20–40°C. Higher temperatures accelerate enzymatic activity, helping to break down organic materials and nutrients more quickly. (*Metcalf & Eddy's Wastewater Engineering*)

- **Low Ammonia/Nitrogen** indicates higher microbial uptake. Ammonia and nitrogen are essential nutrients for microbes. When microbial activity is high, these nutrients are consumed, lowering ammonia and nitrogen levels in the effluent. Lower levels of these nutrients indicate active microbial activity. (*EPA Nutrient Removal Guidelines; Fundamentals of Biological Wastewater Treatment*)

- **BOD (Biochemical Oxygen Demand)** represents the amount of oxygen required by microbes to break down organic matter. A high BOD means there is still a lot of biodegradable organic matter present, meaning microbial activity has not yet occurred. Conversely, a low BOD indicates that microbes have already consumed much of the organic material. (*Water Environment Federation (WEF) Documents*)

### Results from Clustering

For labeling microbial activity levels, I used a subset of the following features from the wastewater dataset:

- Ammonia (mg/L)
- Biological Oxygen Demand (BOD)
- Chemical Oxygen Demand (COD)
- Total Nitrogen (TN)
- Average Temperature
- Maximum Temperature
- Minimum Temperature

The clustering results yielded three distinct classes, each defined by specific feature thresholds:

- **Class 0 (Moderate Activity)**:
  - Ammonia: 40.1 mg/L
  - BOD: 382.8 mg/L
  - COD: 847.6 mg/L
  - Total Nitrogen: 63.6 mg/L
  - Average Temperature: 21.0°C
  
  This class represents moderate biological activity in the wastewater.

- **Class 1 (Low Activity)**:
  - Ammonia: 35.8 mg/L
  - BOD: 335.6 mg/L
  - COD: 751.0 mg/L
  - Total Nitrogen: 60.2 mg/L
  - Average Temperature: 11.2°C
  
  This class indicates low microbial activity, typically associated with cooler temperatures and higher nutrient levels.

- **Class 2 (High Activity)**:
  - Ammonia: 42.6 mg/L
  - BOD: 440.6 mg/L
  - COD: 965.5 mg/L
  - Total Nitrogen: 64.9 mg/L
  - Average Temperature: 13.0°C
  
  This class signifies high microbial activity, where microbial processes are actively consuming organic material and nutrients.