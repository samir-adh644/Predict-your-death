# ❤️ Heart Stroke Prediction using Machine Learning

A simple **Heart Disease/Stroke Risk Prediction** web application built using **Python, Streamlit, Pandas, and Scikit-learn**.

The application allows users to enter medical information through an easy-to-use web interface and predicts whether the person has a **high or low risk of heart disease** using a trained machine learning model.

---

## 📌 Project Overview

This project uses a trained **Naive Bayes (NB)** machine learning model to make predictions.

The Streamlit application:

1. Takes patient information from the user.
2. Converts categorical information into the same format used during model training.
3. Adds missing features with `0`.
4. Arranges the features in the correct order.
5. Scales the input using a saved scaler.
6. Passes the processed data to the trained model.
7. Displays the prediction.

### Prediction Output

* ⚠️ **High Risk of Heart Disease**
* ✅ **Low Risk of Heart Disease**

> **Note:** This application is for educational and demonstration purposes only. It should not be used as a medical diagnosis or as a replacement for professional medical advice.

---

## 🛠️ Technologies Used

* **Python**
* **Streamlit** – Web application framework
* **Pandas** – Data processing
* **Joblib** – Loading saved machine learning objects
* **Scikit-learn** – Machine learning model and preprocessing

---

## 📂 Project Structure

```text
Heart-Stroke-Prediction/
│
├── app.py
├── NB.pkl
├── scaler.pkl
├── columns.pkl
├── README.md
└── requirements.txt
```

### File Description

| File               | Description                              |
| ------------------ | ---------------------------------------- |
| `app.py`           | Main Streamlit application               |
| `NB.pkl`           | Saved Naive Bayes machine learning model |
| `scaler.pkl`       | Saved feature scaler                     |
| `columns.pkl`      | Saved list of expected feature columns   |
| `requirements.txt` | Required Python libraries                |
| `README.md`        | Project documentation                    |

---

## 📊 Input Features

The application asks the user for the following information:

| Feature         | Description                                           |
| --------------- | ----------------------------------------------------- |
| Age             | Patient's age                                         |
| Sex             | Male or Female                                        |
| Chest Pain Type | Type of chest pain                                    |
| Resting BP      | Resting blood pressure                                |
| Cholesterol     | Cholesterol level                                     |
| Fasting BS      | Whether fasting blood sugar is greater than 120 mg/dL |
| Resting ECG     | Resting electrocardiogram result                      |
| Max HR          | Maximum heart rate                                    |
| Exercise Angina | Exercise-induced angina                               |
| Oldpeak         | ST depression value                                   |
| ST Slope        | Slope of the ST segment                               |

---

## 🧠 Machine Learning Model

The application uses a saved **Naive Bayes (NB)** model.

The model is loaded using:

```python
model = joblib.load("NB.pkl")
```

The scaler is loaded using:

```python
scaler = joblib.load("scaler.pkl")
```

The expected feature columns are loaded using:

```python
expected_columns = joblib.load("columns.pkl")
```

These files must be present in the same directory as `app.py`.

---

## 🔄 Prediction Workflow

The prediction process follows these steps:

```text
User Input
    ↓
Create Raw Input Dictionary
    ↓
Convert to Pandas DataFrame
    ↓
Add Missing Columns
    ↓
Reorder Columns
    ↓
Scale Input Data
    ↓
Naive Bayes Model
    ↓
Prediction
    ↓
High Risk / Low Risk
```

---

## 🔤 Handling Categorical Features

Categorical features such as:

* Sex
* Chest Pain Type
* Resting ECG
* Exercise Angina
* ST Slope

are converted into dummy/one-hot encoded columns.

For example, if the user selects:

```text
Sex = M
```

the application creates:

```text
Sex_M = 1
```

Other sex-related columns that are expected by the model but were not selected are filled with:

```text
0
```

This is handled using:

```python
for col in expected_columns:
    if col not in input_df.columns:
        input_df[col] = 0
```

The columns are then arranged in exactly the same order as the training data:

```python
input_df = input_df[expected_columns]
```

---

## 📏 Feature Scaling

Before making a prediction, the input is passed through the saved scaler:

```python
scaled_input = scaler.transform(input_df)
```

This is important because the model was trained using scaled data.

The **same scaler used during training** should always be used during prediction.

---

## 🚀 Installation

### 1. Clone or Download the Project

Download the project files to your computer.

Then open a terminal inside the project folder.

---

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

---

### 3. Install Required Libraries

Create a file named:

```text
requirements.txt
```

Add:

```text
streamlit
pandas
joblib
scikit-learn
```

Then install the dependencies:

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Application

Make sure the following files are in the same folder:

```text
app.py
NB.pkl
scaler.pkl
columns.pkl
```

Run:

```bash
streamlit run app.py
```

Streamlit will start the application and provide a local URL, usually similar to:

```text
http://localhost:8501
```

Open the URL in your browser.

---

## 🖥️ How to Use

### Step 1

Run the Streamlit application:

```bash
streamlit run app.py
```

### Step 2

Enter the patient's information:

* Age
* Sex
* Chest Pain Type
* Resting Blood Pressure
* Cholesterol
* Fasting Blood Sugar
* Resting ECG
* Maximum Heart Rate
* Exercise Angina
* Oldpeak
* ST Slope

### Step 3

Click:

```text
Predict
```

### Step 4

The application displays either:

```text
⚠️ High Risk of Heart Disease
```

or:

```text
✅ Low Risk of Heart Disease
```

---

## ⚠️ Important Notes

### 1. Keep the model files

Do not delete or rename:

```text
NB.pkl
scaler.pkl
columns.pkl
```

unless you also update the Python code.

### 2. Use the same preprocessing

The preprocessing used during prediction must match the preprocessing used during model training.

### 3. Medical Disclaimer

This project is intended for **educational and machine learning demonstration purposes**. The prediction is not a medical diagnosis.

Always consult a qualified healthcare professional for medical decisions.

---


