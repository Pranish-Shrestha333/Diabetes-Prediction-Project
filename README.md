![](UTA-DataScience-Logo.png)

#Diabetes Prediction using Neural Networks

One Sentence Summary: A deep learning pipeline developed in WSL to predict Type 2 Diabetes risk with 70.78% accuracy using clinical health metrics and median-imputed data.

## Overview

I developed this project to evaluate the efficacy of Neural Networks in predicting Type 2 Diabetes using patient health metrics. Rather than focusing solely on model accuracy, I prioritized **data integrity and clinical relevance**. By working in a WSL (Ubuntu) environment, I implemented a custom preprocessing pipeline to address medically impossible data points (such as zero-value BMIs) within the [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database). The final model achieved a **70.78% accuracy**, successfully identifying Glucose and BMI as the most significant physiological indicators.


## Summary of Workdone

### 1. Data Engineering & Cleaning
* **Source:** Utilized the [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database) to analyze 768 patient records with 8 clinical features.
* **Cleaning:** Addressed data quality issues by identifying medically impossible `0` values in features like **BMI, Blood Pressure, and Glucose**. These were handled using **Median Imputation** to maintain dataset integrity without losing valuable samples.
* **Normalization:** Implemented **StandardScaler** to ensure all features (like Age vs. Insulin) were on the same scale, preventing the Neural Network from being biased toward higher-magnitude variables.

### 2. Neural Network Architecture
* **Model Type:** Built a **Sequential Deep Learning Model** using TensorFlow/Keras.
* **Layers:** Designed a 3-layer architecture:
    * **Input Layer:** 12 neurons with ReLU activation to capture initial feature patterns.
    * **Hidden Layer:** 8 neurons with ReLU activation for non-linear complexity.
    * **Output Layer:** 1 neuron with Sigmoid activation for binary classification (0 or 1).
* **Optimization:** Used the **Adam Optimizer** and **Binary Cross-Entropy** loss function, training for 150 epochs with a batch size of 10.

### 3. Evaluation & Insights
* **Results:** Achieved a **70.78% accuracy** on the unseen test set (20% split).
* **Clinical Relevance:** The model confirmed a high correlation between **Glucose/BMI** and diabetes risk, providing a data-driven justification for traditional medical diagnostic focus areas.
      
#### Preprocessing / Clean up

* **Missing Value Imputation:** Medically impossible `0` values in Glucose, Blood Pressure, Skin Thickness, Insulin, and BMI were replaced with the **Median** of their respective columns.
* **Feature Scaling:** Applied **StandardScaler** to normalize the range of all features, ensuring the Neural Network treats all medical metrics with equal importance.

#### Data Visualization

* **Correlation Heatmap:** Used to identify that Glucose has the strongest linear relationship with diabetes.
* **Feature Importance Bar Chart:** Created to show the ranking of medical factors, with Glucose and BMI at the top.
  <img width="841" height="547" alt="image" src="https://github.com/user-attachments/assets/c2ed73fb-213a-4fe1-9606-aca840b22880" />

  <img width="846" height="714" alt="image" src="https://github.com/user-attachments/assets/950789ac-8674-442c-9552-769a2379d227" />



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
  <img width="691" height="547" alt="image" src="https://github.com/user-attachments/assets/748fe23c-6a04-4c81-a375-185b945eec4c" />

  
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







