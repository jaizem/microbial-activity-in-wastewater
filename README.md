# Machine Learning Project: Classification & Analysis

This project satisfies the requirements of a supervised machine learning module by applying classification techniques to **two distinct datasets**, each representing a separate subproject with unique objectives and challenges:

- [**Diabetes Prediction**](#diabetes-prediction)  
  Focused on classifying individuals as diabetic or non-diabetic using health metrics such as glucose levels, BMI, and insulin. This dataset required addressing class imbalance and evaluating model effectiveness across various metrics.

- [**Labeling Microbial Activity in Wastewater**](#labeling-microbial-activity-in-wastewater)  
  A multiclass classification task to label wastewater samples based on microbial activity levels, using chemical and temperature-based features. This project involved clustering, environmental feature analysis, and assessing generalization performance across models.

Each subproject has its own dedicated [Overview](#overview) section and analysis, organized under the titles above for clarity and structure.

## Overview

## Diabetes Prediction
The purpose of this project is to analyze and classify diabetes data using machine learning models, with the goal of predicting whether an individual has diabetes based on a set of health-related features. The dataset consists of 768 samples, with an imbalanced class distribution of approximately 500 non-diabetic and 250 diabetic cases. To address the class imbalance, **SMOTE (Synthetic Minority Over-sampling Technique)** was applied to balance the data and improve model performance.

The analysis involved exploring feature correlations, including the strong relationships between **glucose**, **insulin**, **BMI**, and **age**, which were key indicators for predicting diabetes. Feature engineering was followed by the application of five machine learning models: **Gaussian Naive Bayes**, **Logistic Regression**, **Decision Tree**, **Support Vector Classifier (SVC)**, and **K-Nearest Neighbors (KNN)**. These models were evaluated based on accuracy, precision, recall, F1 score, and cross-validation performance.

The results revealed that **Gaussian Naive Bayes** was the most consistent performer across all metrics, closely followed by **Logistic Regression**. **SVC** showed strong generalization capabilities, while **Decision Tree** and **KNN** exhibited slightly weaker performance. The application of cross-validation helped in assessing model stability, particularly with the imbalanced class distribution.

Overall, this project demonstrates the ability to apply machine learning techniques to a health-related dataset, providing insights into diabetes classification and highlighting the importance of model selection and class balancing.

--- 

## Labeling Microbial Activity in Wastewater

The purpose of this project is to analyze and classify microbial activity levels in wastewater using various machine learning models. The dataset, containing 1,382 samples, was evenly distributed across three classes: **low**, **medium**, and **high** microbial activity. The analysis involves data preprocessing, feature exploration, and dimensionality reduction, along with class balancing to optimize model performance. The features investigated include chemical oxygen demand (COD), biological oxygen demand (BOD), ammonia, nitrogen, and temperature metrics.

This project utilizes machine learning models, including **Logistic Regression**, **Gaussian Naive Bayes**, **Support Vector Classifier (SVC)**, **K-Nearest Neighbors (KNN)**, and **Decision Tree**, to predict microbial activity levels based on the wastewater characteristics. Through this process, key insights were gained regarding the relationships between features such as temperature, ammonia, and organic matter, with microbial activity levels.

The results showed that **Logistic Regression** consistently outperformed other models with the highest accuracy, precision, recall, and F1 score. **SVC** and **Gaussian Naive Bayes** followed closely, while **KNN** and **Decision Tree** exhibited a more significant drop in performance. These findings highlight the importance of selecting the most suitable models based on dataset characteristics and the need for balanced class distributions.

This project also aims to provide a deeper understanding of microbial activity in wastewater, using key environmental factors to predict activity levels, and applying machine learning techniques to improve classification efficiency.

## Environment Setup

### Step-by-Step Instructions for the Environment

1. **Create a Conda Environment:**
   To set up the project environment, we will be using Conda. If you don't have Conda installed, you can install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) or [Anaconda](https://www.anaconda.com/products/individual).

   Once Conda is installed, open a terminal (or Anaconda Prompt) and run the following command to create a new environment named `CSB320`:

   ```bash
   conda env create -f requirements.yml
   ```
   This command will create a new environment and automatically install all the required dependencies listed in the requirements.yml file.

2. **Activate the Conda Environment:**
    After the environment is created, activate it by running:
    ```bash
    conda activate CSB320
    ```
    This ensures that you are using the correct Python environment for the project.

3. **Install Dependencies (If Required):**
    If for any reason you need to install additional dependencies or update the environment later, you can use the following command:

    ```bash
    conda env update -f requirements.yml
    ```
    This will ensure that all dependencies are installed and up-to-date based on the requirements.yml file.

4. **Jupyter Notebook Setup (Optional):**
    Once the environment is activated, you can open a Jupyter Notebook to work on the project. Simply run the following command:

    ```bash
    jupyter notebook
    ```
    This will launch Jupyter in your default browser, and you can start working on the notebooks for the project.

# Installing Dependencies Using `requirements.yml`

To install the dependencies, you should have the `requirements.yml` file provided. It includes a list of all the necessary packages and versions for the project. Below is a breakdown of the key dependencies included in the `requirements.yml` file for setting up the environment.

## Dependencies Breakdown

### 1. **Python 3.9**
This project uses **Python 3.9** for compatibility with the required packages.

### 2. **Pandas, Numpy, and Scikit-learn**
- **Pandas**: Used for data manipulation.
- **Numpy**: Used for numerical operations.
- **Scikit-learn**: Provides machine learning algorithms.

### 3. **Matplotlib and Seaborn**
- **Matplotlib**: A plotting library used for data visualization.
- **Seaborn**: A visualization library built on top of Matplotlib for statistical graphics.

### 4. **Imbalanced-learn**
This library is used for handling imbalanced datasets, including techniques like SMOTE (Synthetic Minority Over-sampling Technique).

### 5. **Stable-baselines3 and Gymnasium**
- **Stable-baselines3**: A library for reinforcement learning.
- **Gymnasium**: Provides environments for reinforcement learning simulations.

### 6. **Jupyter**
**Jupyter Notebooks** are used for data analysis and experimentation.

### 7. **NLTK**
The **Natural Language Toolkit (NLTK)** is useful for processing text data.

### 8. **Nbqa**
This tool is used to run **black** (for code formatting) and **flake8** (for linting) on Jupyter Notebooks.

---

## Additional Notes

Once you've installed all dependencies and activated the environment, you can start using the Jupyter notebooks for further analysis.

The environment is already set up with the required libraries, so you should be good to go once you've activated it.

---

## Troubleshooting

If you encounter issues with package versions or missing dependencies, try updating the environment or installing the missing packages using `conda` or `pip`. For example:

### Using Conda:
```bash
conda install <package-name>
```

### Using Pip:
```bash
pip install <package-name>
```

If you're still having trouble, feel free to open an issue in the GitHub repository.

