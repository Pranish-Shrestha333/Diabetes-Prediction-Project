![](UTA-DataScience-Logo.png)

#Diabetes Prediction using Neural Networks

* **Summary**This project implements a Sequential Neural Network to predict the likelihood of diabetes in patients based on clinical metrics. This study uses the [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database) originally from the National Institute of Diabetes and Digestive and Kidney Diseases.

## Overview
* **The Task:** Binary classification of diabetic vs. non-diabetic patients using 8 physiological features.
* **My Approach:** Built using a WSL-based workflow, I performed data cleaning on medically impossible zero-values (BMI, Blood Pressure) and utilized a 3-layer Neural Network (12-8-1 architecture) with TensorFlow/Keras.
* **Performance:** Achieved a **71% test accuracy** and an AUC of **0.70**. My analysis confirms that **Glucose** and **BMI** are the most significant medical predictors in this dataset.


## Summary of Workdone

* **Source:** [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)
* **Input:** CSV file with 8 medical features (Glucose, Blood Pressure, BMI, Age, etc.).
* **Output:** Binary label (0 for healthy, 1 for diabetic).
* **Size:** 768 patient records.
* **Split:** 80% Training, 20% Testing.


* Data:
  * Type: For example
    * Input: medical images (1000x1000 pixel jpegs), CSV file: image filename -> diagnosis
    * Input: CSV file of features, output: signal/background flag in 1st column.
  * Size: How much data?
  * Instances (Train, Test, Validation Split): how many data points? Ex: 1000 patients for training, 200 for testing, none for validation

#### Preprocessing / Clean up

* **Missing Value Imputation:** Medically impossible `0` values in Glucose, Blood Pressure, Skin Thickness, Insulin, and BMI were replaced with the **Median** of their respective columns.
* **Feature Scaling:** Applied **StandardScaler** to normalize the range of all features, ensuring the Neural Network treats all medical metrics with equal importance.

#### Data Visualization

* **Correlation Heatmap:** Used to identify that Glucose has the strongest linear relationship with diabetes.
* **Feature Importance Bar Chart:** Created to show the ranking of medical factors, with Glucose and BMI at the top.

### Problem Formulation

* **Model:** Sequential Neural Network.
* **Architecture:** * Input Layer: 12 neurons (ReLU)
    * Hidden Layer: 8 neurons (ReLU)
    * Output Layer: 1 neuron (Sigmoid)
* **Loss Function:** Binary Cross-Entropy.
* **Optimizer:** Adam.

### Training

* **Epochs:** 150
* **Batch Size:** 10
* **Platform:** Developed in a WSL (Ubuntu) environment using TensorFlow/Keras.
* **Early Stopping:** Monitored validation loss to prevent overfitting.
  
### Performance Comparison

* **Final Test Accuracy:** 70.78% (Rounded to 71% in summary).
* **AUC-ROC Score:** 0.70.
* **Evaluation:** Generated a Confusion Matrix to analyze True Positives and False Negatives, confirming the model's reliability in a clinical context.
  
### Conclusions

* Neural Networks are effective at finding non-linear patterns in patient health data that simple regressions might miss.
* Feature engineering (cleaning the zero-values) was the most critical step in improving accuracy from 65% to 71%.

### Future Work

* **Hyperparameter Tuning:** Experiment with different dropout layers to reduce variance.
* **Expanded Data:** Incorporate more diverse datasets to improve the model's generalization across different ethnicities.

## How to reproduce results

1. **Environment:** Use a WSL (Ubuntu) terminal with Python 3.10+.
2. **Setup:** - Clone this repo: `git clone https://github.com/Pranish-Shrestha333/Diabetes-Prediction-Project..git`
   - Install requirements: `pip install -r requirements.txt`
3. **Execution:** Open `notebooks/Diabetes_Kaggle_Project.ipynb` in Jupyter Lab and run all cells to reproduce the training and evaluation metrics.

### Overview of files in repository

* 📁 **data/**: Contains the `train.csv` (raw data) and `final_submission.csv` (model predictions).
* 📁 **notebooks/**: Contains `Diabetes_Kaggle_Project.ipynb`, the complete pipeline from cleaning to Neural Network evaluation.
* 📄 **README.md**: Project documentation and summary of findings.

### Software Setup
* **TensorFlow/Keras:** For building and training the Neural Network.
* **Scikit-Learn:** For data scaling and train-test splitting.
* **Pandas/NumPy:** For data manipulation and handling missing values.
* **Matplotlib/Seaborn:** For medical correlation visualizations.

#### Performance Evaluation

* **Confusion Matrix:** Analyzed to ensure a balance between precision and recall, specifically focusing on minimizing False Negatives which are critical in medical diagnostics.
* **ROC Curve:** The Area Under the Curve (AUC) of 0.70 indicates the model has a strong ability to distinguish between diabetic and non-diabetic cases.

## Citations

"Pima Indians Diabetes Database. (2016). UCI Machine Learning Repository / Kaggle..







