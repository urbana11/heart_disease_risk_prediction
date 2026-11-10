# Heart Disease Prediction Using Machine Learning

## About the Project

Heart Disease Prediction is a machine learning project that predicts whether a person may have heart disease based on their medical information.

The main goal is to analyze health-related data using machine learning and predict the possible presence of heart disease. We developed this project using **Python**, **Logistic Regression**, and the **Cleveland Heart Disease Dataset**.

The project includes a **Flask API** that accepts medical information and returns a prediction.

## How the Project Works

1. Collect heart disease data from the dataset.
2. Explore and prepare the data for training.
3. Train a machine learning model using Logistic Regression.
4. Test the model to evaluate its performance.
5. Save the trained model for future predictions.
6. Use Flask to provide predictions through an API.

## Dataset

We used the **Cleveland Heart Disease Dataset**, which contains:

- **303** patient records
- **13** medical input features
- **1** target column indicating the presence or absence of heart disease

Some input features include age, sex, chest pain type, resting blood pressure, cholesterol level, maximum heart rate, exercise-induced angina, and number of major blood vessels.

These features help the model identify patterns related to heart disease.

## Machine Learning Model

We trained the model using **Logistic Regression**, a classification algorithm that predicts one of two outcomes:

- `0`: No heart disease
- `1`: Heart disease

The dataset was split into **80% training data** and **20% testing data**.

## Model Performance

| Evaluation | Result |
|---|---:|
| Total records | 303 |
| Training records | 242 |
| Testing records | 61 |
| Accuracy | 80.33% |
| ROC-AUC | Approximately 0.904 |

These results describe performance on the test dataset and do not guarantee accurate predictions for every person.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data handling and analysis |
| NumPy | Numerical operations |
| Scikit-learn | Model building and training |
| Jupyter Notebook | Data analysis and model training |
| Flask | Prediction API |
| Flask-CORS | Cross-origin request handling |

## Project Structure

```text
Heart-Disease-Prediction/
├── app.py
├── heartDiseases.ipynb
├── heart_disease_data.csv
├── prediction_model.pkl
├── requirements.txt
└── README.md
```

## Installation and Setup

### Step 1: Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

### Step 2: Open the project folder

```bash
cd YOUR_REPOSITORY
```

### Step 3: Install required packages

```bash
pip install flask flask-cors pandas numpy scikit-learn notebook
```

> **Compatibility note:** If your saved model was created with scikit-learn 1.2.2, use a compatible Python environment (such as Python 3.10) and matching scikit-learn version when loading it.

### Step 4: Run the Flask application

```bash
python app.py
```

The local server should start at:

```text
http://127.0.0.1:5000
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | Displays a welcome message |
| `GET` | `/test` | Checks whether the API is working |
| `POST` | `/predict` | Predicts the possibility of heart disease |

## Example Prediction

Send a `POST` request to:

```text
http://127.0.0.1:5000/predict
```

Example JSON input:

```json
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
```

The API returns a prediction indicating either:

- `The Person does not have a Heart Disease`
- `The Person has Heart Disease`

The exact JSON response structure depends on the version of `app.py` used.

## Project Objectives

This project explores how machine learning can be applied to healthcare-related problems. Through it, we learned to:

- Work with a real-world medical dataset.
- Analyze and prepare data.
- Train a classification model.
- Evaluate model performance.
- Save and reuse a trained model.
- Build a Flask API for predictions.

## Limitations

This project is for **educational purposes only**. Predictions are **not medical diagnoses** and must not replace professional medical advice.

The model was tested on a small dataset and requires further evaluation using independent patient data before any real-world medical application.

## Authors

**Umme Ara Urbana**  
Registration No: 22201216

**Tabeeb Tazwar Ahmad**  
Registration No: 22201218

Department of Computer Science and Engineering  
**University of Asia Pacific**  
Dhaka, Bangladesh

## References

1. [Cleveland Heart Disease Dataset — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/45/heart+disease)
2. Detrano, R., et al. (1989). *International application of a new probability algorithm for the diagnosis of coronary artery disease*. American Journal of Cardiology.
3. [Scikit-learn Documentation](https://scikit-learn.org/stable/)
4. [Flask Documentation](https://flask.palletsprojects.com/)
