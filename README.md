# Customer Churn Prediction Using ANN and Streamlit

# project Overview

This project builds a deep learning model using Artificial Neural Networks (ANNs) to predict customer churn. The model analyzes customer attributes like age, credit score, account balance, and transaction behavior to determine the likelihood of churn.

It involves:

### 1. Data Preprocessing:
Cleaning and preparing data.

### 2. Model Training:
Building and training an ANN model.

### 3. Hyperparameter Tuning:
Optimizing the model for better performance.

### 4. Monitoring & Visualization:
Using TensorBoard for real-time tracking.

### 5.Prediction & Deployment:
Using the model in a Streamlit web app.

# Project Structure
📂 Customer-Churn-Prediction-ANN
│-- 📜 README.md                # Project Documentation
│-- 📜 requirements.txt          # Required Dependencies
│-- 📂 data                      # Dataset Files
│   ├── Churn_Modelling.csv
│-- 📂 models                    # Saved Model & Encoders
│   ├── model.h5
│   ├── label_encoder_gender.pkl
│   ├── onehot_encoder_geo.pkl
│   ├── scaler.pkl
│-- 📂 scripts                   # Training & Prediction Scripts
│   ├── experiment.py            # Data Preprocessing & ANN Model
│   ├── hypertuning.py           # Hyperparameter Optimization
│   ├── prediction.py            # Prediction Logic
│-- 📂 logs                      # Training Logs for TensorBoard
│-- 📜 app.py                    # Streamlit App

# Dataset

The dataset used is Churn_Modelling.csv, which contains customer information, including:
- Demographics: Geography, Gender, Age
- Financial Information: Balance, Credit Score, Estimated Salary
- Banking Activity: Number of Products, Tenure, Credit Card, Active Member
- Target Variable: Exited (1 = Churned, 0 = Retained)

#  Data Preprocessing:
Before training the model, the dataset undergoes several preprocessing steps:
### Dropping Unnecessary Columns: 
Customer ID and name are removed as they don’t contribute to predictions.
### Encoding Categorical Variables:
 - Label Encoding for Gender converts text values into numerical ones.
 - One-Hot Encoding for Geography ensures categorical values are represented properly.
### Feature Scaling: 
Standardizing numerical values improves model performance.
### Saving Encoders & Scalers: 
These preprocessing components are stored for consistent input transformation during predictions.

# Model Training with ANN
The ANN model consists of:
### Input Layer: 
Takes in customer details like age, balance, and tenure.
### Hidden Layers: 
Utilize ReLU activation functions to capture complex patterns.
### Output Layer: 
Uses Sigmoid activation to predict the probability of customer churn.
### The model is trained with:
- Adam optimizer : Efficiently adjusts learning rates for faster convergence.
- Binary cross-entropy loss : Suitable for binary classification problems.
- Early Stopping & TensorBoard Logging : Prevents overfitting and allows real-time monitoring.

# Hyperparameter Tuning
Hyperparameter tuning is performed using GridSearchCV, which systematically tests different configurations of:
- Number of neurons per layer
- Number of hidden layers
- Number of epochs
This optimization ensures the model is fine-tuned for the best accuracy and efficiency.

# Monitoring & Visualization with TensorBoard
To track training performance, TensorBoard is used for real-time visualization and diagnostics. It helps analyze:

### Key Metrics Tracked:

### 1. Bias Histogram:
Displays weight distributions across network layers, ensuring stable learning.
### 2.Epoch Accuracy:
Measures the accuracy improvement over training epochs.
### 3. Epoch Loss: 
Shows how effectively the model minimizes errors.
### 4. Evaluation Accuracy vs. Iterations: 
Compares accuracy across training and validation data.

### Sample TensorBoard Visualizations:
The following visualizations illustrate different aspects of training:
 - Helps in diagnosing model stability and weight distributions.
 - Shows accuracy trends over time, ensuring model is learning properly.
 - Helps in understanding performance differences between training and validation data.

TensorBoard is a crucial tool for detecting overfitting, learning rate issues, and model convergence.

To launch TensorBoard:

```bash
%load_ext tensorboard
%tensorboard --logdir logs/fit
```


<img width="1440" alt="Image" src="https://github.com/user-attachments/assets/6b96146b-4b17-4d01-93e5-98529851805c" />
<img width="1440" alt="Image" src="https://github.com/user-attachments/assets/89732ec4-7eea-41e0-b185-79ae238312ee" />
<img width="1440" alt="Image" src="https://github.com/user-attachments/assets/2adc6dcc-a900-41fc-941e-0fb19173a3b4" />

# Making Predictions
Once trained, the model can predict customer churn based on new user inputs. The prediction process involves:
### 1. Loading Pre-trained Model & Encoders: 
The trained ANN and saved encoders ensure consistency.
### 2.Preprocessing User Input: 
Inputs are encoded and scaled similarly to the training phase.
### 3.Running Prediction: 
The model computes churn probability.
### 4.Interpreting Results:
 - If Churn Probability > 0.5 → Customer is likely to churn.
 - Otherwise → Customer is likely to stay.

# Running the Streamlit App

The model is deployed using Streamlit, providing a web interface for predictions. To launch:
```bash
streamlit run app.py
```
Users can input customer details and instantly get churn predictions through a user-friendly dashboard.

# Conclusion

This project provides an end-to-end AI-powered solution for predicting customer churn. By integrating data preprocessing, ANN training, hyperparameter tuning, and real-time monitoring with TensorBoard, the model offers a scalable, efficient approach to understanding and mitigating customer attrition.







