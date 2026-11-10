Heart Disease Prediction Using Machine Learning

About the Project

Heart Disease Prediction is a machine learning project that predicts whether a person may have heart disease based on their medical information.

The main goal of this project is to use machine learning to analyze health-related data and make predictions about the possibility of heart disease.

We developed this project using Python and Logistic Regression with the Cleveland Heart Disease Dataset.

The project also includes a Flask API that allows users to submit medical information and receive a prediction.

How the Project Works

The project follows a simple process:

Collect heart disease data from the dataset.

Explore and prepare the data for training.

Train a machine learning model using Logistic Regression.

Test the model to check its performance.

Save the trained model for future predictions.

Use Flask to provide predictions through an API.

Dataset

We used the Cleveland Heart Disease Dataset, which contains:

303 patient records.

13 medical input features.

1 target column indicating the presence or absence of heart disease.

Some of the features used by the model include:

Age

Sex

Chest pain type

Resting blood pressure

Cholesterol level

Maximum heart rate

Exercise-induced angina

Number of major blood vessels

These features help the model identify patterns related to heart disease.

Machine Learning Model

We used Logistic Regression to train the prediction model.

Logistic Regression is a classification algorithm that predicts one of two possible outcomes:

0: No heart disease

1: Heart disease

The dataset was divided into two parts:

80% for training the model.

20% for testing the model.

Model Performance

Our model achieved the following results on the test dataset:

Evaluation

Result

Total records

303

Training records

242

Testing records

61

Accuracy

80.33%

ROC-AUC

Approximately 0.904

These results show how the model performed on our test data. They do not guarantee accurate predictions for every person.

Technologies Used

Python – Main programming language.

Pandas – For handling and analyzing data.

NumPy – For numerical operations.

Scikit-learn – For building and training the machine learning model.

Jupyter Notebook – For data analysis and model training.

Flask – For creating the prediction API.

Flask-CORS – For handling cross-origin requests.

Project Structure

Heart-Disease-Prediction/
│
├── app.py
├── heartDiseases.ipynb
├── heart_disease_data.csv
├── prediction_model.pkl
├── requirements.txt
└── README.md

Installation and Setup

Step 1: Clone the Repository

git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git

Step 2: Open the Project Folder

cd YOUR_REPOSITORY

Step 3: Install Required Packages

pip install flask flask-cors pandas numpy scikit-learn notebook

Step 4: Run the Flask Application

python app.py

The server will start at:

http://127.0.0.1:5000

API Endpoints

Method

Endpoint

Description

GET

/

Displays a welcome message.

GET

/test

Checks whether the API is working.

POST

/predict

Predicts the possibility of heart disease.

Example Prediction

Send a POST request to:

http://127.0.0.1:5000/predict

Example input:

{
  "age": 62,
  "sex": 0,
  "cp": 0,
  "trestbps": 140,
  "chol": 268,
  "fbs": 0,
  "restecg": 0,
  "thalach": 160,
  "exang": 0,
  "oldpeak": 3.6,
  "slope": 0,
  "ca": 2,
  "thal": 2
}

The API returns one of the following predictions:

"The Person does not have a Heart Disease"

"The Person has Heart Disease"

Project Objectives

The objective of this project is to understand how machine learning can be used in healthcare-related applications.

Through this project, we learned how to:

Work with a real-world medical dataset.

Analyze and prepare data.

Train a machine learning classification model.

Evaluate model performance.

Save and reuse a trained model.

Build a Flask API for making predictions.

Limitations

This project is developed for educational purposes. Its predictions are not medical diagnoses and should not be used as a replacement for professional medical advice.

The model has been tested on a small dataset and needs further testing with independent patient data before any real-world medical use.

Authors

Umme Ara Urbana
Registration No: 22201216

Tabeeb Tazwar Ahmad
Registration No: 22201218

Department of Computer Science and Engineering
University of Asia Pacific
Dhaka, Bangladesh

References

Cleveland Heart Disease Dataset – UCI Machine Learning Repository.

Detrano et al. (1989). International application of a new probability algorithm for the diagnosis of coronary artery disease.

Scikit-learn Documentation

Flask Documentation
