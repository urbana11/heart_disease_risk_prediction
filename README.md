[README.md](https://github.com/user-attachments/files/34587557/README.md)
# Heart Disease Risk Prediction Using Machine Learning

A machine learning project that predicts the presence or absence of heart disease from 13 clinical features. The project trains a **Logistic Regression** classifier on the Cleveland heart disease dataset and provides a simple **Flask REST API** for predictions.

> **Important:** This is an educational prototype, not a medical diagnostic tool. Its output should not be used to make clinical decisions.

## Project overview

The dataset contains **303 patient records**, **13 input features**, and a binary target (`0` = no heart disease, `1` = heart disease). The training notebook explores the data, checks missing values, splits the dataset, trains a Logistic Regression model, and saves it as `prediction_model.pkl`.

### Reported results

| Metric | Value |
|---|---:|
| Dataset size | 303 records |
| Training set | 242 records (80%) |
| Test set | 61 records (20%) |
| Test accuracy | **80.33%** (49/61 correct) |
| Test ROC-AUC | **~0.904** |
| True negatives (TN) | 22 |
| False positives (FP) | 6 |
| False negatives (FN) | 6 |
| True positives (TP) | 27 |

The split uses `test_size=0.2`, `stratify=Y`, and `random_state=2`. The model is `LogisticRegression(max_iter=1000)`. The notebook passes the original feature values directly to the model; it **does not apply feature scaling**, even though some scaler classes are imported.

These results are from a single held-out split, not cross-validation or external clinical validation.

## Features

The model uses these input columns **in this order**:

| Feature | Description |
|---|---|
| `age` | Age in years |
| `sex` | Sex (dataset-encoded) |
| `cp` | Chest pain type |
| `trestbps` | Resting blood pressure |
| `chol` | Serum cholesterol |
| `fbs` | Fasting blood sugar indicator |
| `restecg` | Resting electrocardiogram result |
| `thalach` | Maximum heart rate achieved |
| `exang` | Exercise-induced angina |
| `oldpeak` | ST depression induced by exercise |
| `slope` | Slope of peak exercise ST segment |
| `ca` | Number of major vessels shown by fluoroscopy |
| `thal` | Thalassemia / perfusion test category |

The `target` column is the prediction label and **must not** be included in API requests.

## Repository structure

```text
.
├── app.py                    # Flask API
├── heartDiseases.ipynb       # Training and evaluation notebook
├── heart_disease_data.csv    # Dataset
├── prediction_model.pkl      # Serialized trained model
├── requirements.txt          # Dependencies (if included)
└── README.md
```

Your notebook may be named `heartDiseases(2).ipynb` after downloading; either name works.

## Installation

**Requirements:** Python 3 and the packages Flask, Flask-CORS, pandas, NumPy, scikit-learn, and Jupyter (for the notebook).

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
python -m venv .venv
```

Activate the environment:

```bash
# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

Install dependencies:

```bash
pip install flask flask-cors pandas numpy scikit-learn notebook
```

If the repository includes a compatible `requirements.txt`, you can use `pip install -r requirements.txt` instead. The saved model was created with scikit-learn **1.2.2**; using that version is recommended for compatibility when loading the pickle file.

## Run the prediction API

Ensure `prediction_model.pkl` is in the same working directory as `app.py`, then run:

```bash
python app.py
```

The Flask development server normally starts at `http://127.0.0.1:5000`.

### Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/` | Welcome message |
| `GET` | `/test` | Simple API test |
| `POST` | `/predict` | Predict a binary heart disease label |

### Example prediction request

```bash
curl -X POST http://127.0.0.1:5000/predict \
  -H "Content-Type: application/json" \
  -d '{
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
  }'
```

The current implementation returns a **JSON string**, not a JSON object. Depending on the prediction, the response is one of:

```json
"The Person does not have a Heart Disease"
```

or

```json
"The Person has Heart Disease"
```

The current API does not return a probability score, validate the supplied fields, or provide structured error responses.

## Train the model again

1. Open `heartDiseases.ipynb` (or `heartDiseases(2).ipynb`) in Jupyter Notebook.
2. Keep `heart_disease_data.csv` in the notebook's working directory.
3. Run the cells in order to inspect the data, train the classifier, and calculate test accuracy.
4. The serialization cell writes a new `prediction_model.pkl` file.

```bash
jupyter notebook
```

**Note:** Retraining can yield different convergence behavior across scikit-learn versions. Only replace the existing model file after checking its evaluation results.

## Limitations and future improvements

- Evaluate with stratified cross-validation and report variability across folds.
- Add precision, recall, F1-score, ROC-AUC, and confusion-matrix reporting to the notebook.
- Consider preprocessing with a training-only pipeline, including appropriate scaling and categorical encoding.
- Validate incoming API values and enforce the model's expected feature schema.
- Return prediction probabilities and structured JSON responses.
- Disable Flask debug mode and restrict CORS before any production deployment.
- Test on independent patient populations before considering clinical use.

## Authors

**Umme Ara Urbana** — Registration No. 22201216  
**Tabeeb Tazwar Ahmad** — Registration No. 22201218  
Department of Computer Science and Engineering  
**University of Asia Pacific**, Dhaka, Bangladesh

## References

- Detrano, R., et al. (1989). *International application of a new probability algorithm for the diagnosis of coronary artery disease*. The American Journal of Cardiology, 64(5), 304–310. https://doi.org/10.1016/0002-9149(89)90524-9
- Mohan, S., Thirumalai, C., & Srivastava, G. (2019). *Effective heart disease prediction using hybrid machine learning techniques*. IEEE Access, 7, 81542–81554. https://doi.org/10.1109/ACCESS.2019.2923707
- Weng, S. F., Reps, J., Kai, J., Garibaldi, J. M., & Qureshi, N. (2017). *Can machine-learning improve cardiovascular risk prediction using routine clinical data?* PLOS ONE, 12(4), e0174944. https://doi.org/10.1371/journal.pone.0174944
