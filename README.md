# SMS Spam Filtering ML Model

A beginner-friendly machine learning project that classifies text messages as **spam** or **ham** (legitimate). It uses TF-IDF text features and a Multinomial Naive Bayes classifier.

## Features

- Train a text classification model from labeled messages
- Evaluate using accuracy, precision, recall, F1-score, and a confusion matrix
- Save the trained model locally
- Classify messages interactively from the terminal
- Accepts CSV columns named `label` and `message`, or the original UCI column names `v1` and `v2`

## Project structure

```text
spam-filter-ml/
├── spam.csv                 # Dataset you add locally
├── train_model.py           # Trains and evaluates the model
├── spam_classifier.py       # Interactive message classifier
├── requirements.txt
├── README.md
├── .gitignore
└── models/
    └── spam_model.joblib    # Generated after training
```

## Requirements

- Python 3.9 or newer
- Internet access to download the dataset

## Setup

### 1. Create and activate a virtual environment (recommended)

Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Download the dataset

Download the **SMS Spam Collection** dataset from the UCI Machine Learning Repository:

https://archive.ics.uci.edu/dataset/228/sms+spam+collection

Prepare a CSV file named `spam.csv` in this folder with two columns:

```csv
label,message
ham,"Hey, are we still meeting today?"
spam,"Congratulations! You have won a prize. Claim now!"
```

Use the full labeled dataset for meaningful training and evaluation; the two rows above are only an illustration, not a useful training dataset. If using the original UCI file, its columns are commonly named `v1` and `v2`; the training script accepts those column names too, provided the file is a CSV with a header row.

### 4. Train the model

```bash
python train_model.py
```

The script splits the data into training and test sets, trains the pipeline, prints evaluation metrics, and saves the model to `models/spam_model.joblib`.

### 5. Run the spam detector

```bash
python spam_classifier.py
```

Enter any message when prompted. Type `exit` to quit.

## How it works

1. **TF-IDF** converts message text into numeric features.
2. **Multinomial Naive Bayes** learns patterns associated with spam and ham.
3. The model is evaluated on a held-out test set.
4. The trained pipeline is saved with Joblib and reused for predictions.

## Upload to GitHub

Create an empty repository on GitHub, then run these commands from this project directory:

```bash
git init
git add .
git status
git commit -m "Add SMS spam filtering ML model"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/spam-filter-ml.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username. Check `git status` before committing. The dataset and trained model are not included by default; add `spam.csv` locally and train the model. If you want to share the dataset, follow the dataset's license and attribution terms.

## Notes

- Model predictions and confidence values are estimates, not guarantees.
- Accuracy alone can be misleading when spam and ham examples are imbalanced; review precision, recall, and F1-score too.
- Only load Joblib/pickle model files from sources you trust.

## Possible improvements

- Compare Naive Bayes with Logistic Regression
- Build a Streamlit web interface
- Add a confusion-matrix plot
- Deploy a public demo
