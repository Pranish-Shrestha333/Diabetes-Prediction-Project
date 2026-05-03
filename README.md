![](UTA-DataScience-Logo.png)

#Diabetes Prediction using Neural Networks

One Sentence Summary: A deep learning pipeline developed in WSL to predict Type 2 Diabetes risk with 70.78% accuracy using clinical health metrics and median-imputed data.


# 🩺 Diabetes Risk Prediction: Deep Learning & Feature Engineering
**Author:** Pranish Shrestha  
**Course:** DATA 3402 - Spring 2026  
**University:** University of Texas at Arlington  

---

## 📌 Project Overview
This project evaluates the efficacy of **Deep Neural Networks (MLP)** in predicting Type 2 Diabetes using patient health metrics. Rather than focusing solely on baseline accuracy, this project prioritizes **clinical relevance and data integrity**. 

Developed within a **WSL (Ubuntu)** environment, the pipeline addresses the limitations of traditional models by implementing custom feature engineering and a robust preprocessing strategy for the [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database).

### **Key Technical Highlights:**
* **Neural Network Architecture:** Built a 3-layer Sequential model using TensorFlow/Keras, specifically tuned to handle 9-dimensional input vectors.
* **Feature Engineering:** Developed a custom `Age_BMI_Interaction` feature to capture the non-linear risk growth associated with aging and high BMI.
* **Advanced Preprocessing:** Implemented median imputation for medically impossible `0` values in Glucose, Blood Pressure, and BMI.

---

## 📊 Exploratory Data Analysis & Insights

Understanding the physiological drivers of diabetes was crucial for model design. 

### **1. Glucose Distribution & Risk**
![Glucose Density Plot]<img width="872" height="547" alt="image" src="https://github.com/user-attachments/assets/30045393-9d13-4e38-ae1a-92efc7e810a6" />

The density plot reveals that Glucose is the primary differentiator. Patients with higher glucose levels (Class 1) show a distinct distribution shift, confirming it as the most significant predictor.

### **2. Feature Correlations**
![Feature Importance]<img width="846" height="714" alt="image" src="https://github.com/user-attachments/assets/d745539a-2761-4103-8b9b-ca597d6e2674" />

Our correlation analysis identified **Glucose, BMI, and Age** as the top three indicators. This insight led to the creation of the `Age_BMI_Interaction` feature, which boosted the model's ability to find complex patterns in high-risk groups.

---

## 🛠️ Technical Implementation

### **1. Data Engineering & Preprocessing**
* **Imputation:** Medically impossible `0` values in clinical features were replaced with **Median** values to maintain dataset volume while ensuring biological accuracy.
* **Normalization:** Used **StandardScaler** to ensure the Neural Network was not biased toward higher-magnitude variables like Insulin.
* **The "9-Feature" Re-Architecture:** After engineering the new interaction feature, I successfully updated the MLP input layer to accept $N=9$ dimensions, resolving common shape-mismatch errors.

### **2. Neural Network Architecture**
* **Input Layer:** 12 neurons (ReLU) - Optimized for 9 features.
* **Hidden Layer:** 8 neurons (ReLU) - Capturing non-linear medical complexities.
* **Output Layer:** 1 neuron (Sigmoid) - Binary Classification (0 or 1).
* **Optimization:** Adam Optimizer with Binary Cross-Entropy Loss.

---

## 📈 Performance Evaluation

### **Confusion Matrix Analysis**
![Confusion Matrix]<img width="501" height="393" alt="image" src="https://github.com/user-attachments/assets/1659fa86-c1ab-41de-9b9f-da2b49d7f1bd" />

The model achieved a balanced performance, correctly identifying **43 True Positives**. In a clinical context, we prioritized minimizing **False Negatives** (12) to ensure high-risk patients are not overlooked.

### **ROC-AUC Results**
![ROC Curve]<img width="691" height="547" alt="image" src="https://github.com/user-attachments/assets/15c1cd4a-4bbb-4ef4-9fbb-7ff3ccf0c40f" />

The model achieved a final **Test Accuracy of 71%** and an **AUC score of 0.76**. The ROC curve demonstrates a strong "True Positive Rate," significantly outperforming a random baseline and proving the model's predictive reliability.

---

## 🏁 Conclusions
* **Feature Engineering is King:** Cleaning zero-values and adding the Age-BMI interaction improved accuracy from a baseline of 65% to **71%**.
* **Deep Learning Utility:** Neural Networks effectively captured non-linear patterns in patient health data that standard regressions often miss.
* **WSL Workflow:** Utilizing a Linux-based environment ensured a professional-grade version control and package management (pip/venv) workflow.

---

## 🚀 How to Reproduce
1. **Environment:** Use WSL (Ubuntu) with Python 3.10+.
2. **Setup:** ```bash
   git clone [https://github.com/Pranish-Shrestha333/Diabetes-Prediction-Project.git](https://github.com/Pranish-Shrestha333/Diabetes-Prediction-Project.git)
   cd Diabetes-Prediction-Project
   pip install -r requirements.txt
