# Hand Gesture Recognition using Computer Vision & Machine Learning

## 📌 Project Overview

This project focuses on recognizing hand gestures representing **digits (0–9)** and **English letters (A–Z)** using Computer Vision and Machine Learning.

The system uses **MediaPipe Hands** to detect a hand and extract its landmarks. These landmarks are transformed into numerical features and used to train and compare multiple Machine Learning classification models.

## 🎯 Objectives

- Detect a hand from gesture images.
- Extract hand landmarks using MediaPipe.
- Convert landmarks into numerical features.
- Normalize the features to reduce the effect of hand position and size.
- Train and compare multiple Machine Learning models.
- Evaluate models using accuracy and F1-score.
- Save the selected model for future use.

## 🔍 Methodology

### 1. Hand Landmark Extraction

The project uses **MediaPipe Hands** to detect a single hand and extract **21 hand landmarks**.

For every landmark, the system extracts its **x** and **y** coordinates:

**21 landmarks × 2 coordinates = 42 features per sample**

### 2. Feature Normalization

The extracted coordinates are normalized by:

- Translating the landmarks so the wrist (landmark 0) becomes the origin.
- Scaling the coordinates using the maximum distance from the origin.

This reduces sensitivity to the hand's position and scale.

### 3. Dataset

The landmark extraction process produced **2,641 samples** across **36 gesture classes**:

- Digits: `0–9`
- English letters: `A–Z`

The extracted features and labels are stored in `dataset.csv`.

## 🤖 Machine Learning Models

Three classification models were trained and evaluated:

- **Random Forest**
- **Support Vector Machine (SVM)**
- **K-Nearest Neighbors (KNN)**

The data was split into **80% training** and **20% testing**, using stratification and `random_state=42`.

## 📊 Results

| Model | Train Accuracy | Test Accuracy | Train F1 | Test F1 | Training Time |
|---|---:|---:|---:|---:|---:|
| Random Forest | 100.00% | 95.65% | 1.0000 | 0.9500 | 1.47 s |
| SVM | 96.26% | 96.03% | 0.9570 | 0.9523 | 0.09 s |
| K-Nearest Neighbors | 95.27% | 92.82% | 0.9449 | 0.9190 | 0.01 s |

Based on **test accuracy**, SVM achieved **96.03%**, the highest test accuracy among the evaluated models.

The selected model was saved as:

`best_sign_model.pkl`

## 🛠️ Technologies

- Python 3.11
- OpenCV
- MediaPipe
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib

## 📁 Project Structure

```text
hand-gesture-recognition/
├── README.md
├── visualization.ipynb
├── best_sign_model.pkl
├── requirements.txt
├── images/
│   ├── model_comparison.png
│   ├── svm_confusion_matrix.png
│   └── classification_report.png
└── data/
    └── README.md
```

> The original image dataset is not included in this repository. The notebook expects the gesture image dataset to be available locally.

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd hand-gesture-recognition
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Open the notebook

```bash
jupyter notebook visualization.ipynb
```

Run the notebook cells to extract landmarks, create `dataset.csv`, train the models, compare their performance, and save the selected model.

## 📈 Evaluation

The project evaluates performance using:

- Training Accuracy
- Test Accuracy
- Macro F1-Score
- Training Time
- Confusion Matrix
- Per-class Precision, Recall, and F1-Score

## 💡 Key Takeaways

- Hand landmarks provide a compact numerical representation for gesture classification.
- Landmark normalization reduces the effect of hand position and scale.
- Three Machine Learning approaches were compared.
- SVM achieved **96.03% test accuracy** in this experiment and was saved as the selected model.

## 🚀 Future Work

- Real-time gesture recognition using a webcam.
- Integration into a real-time application.
- Improving recognition of visually similar gestures.
- Further feature engineering and hyperparameter experimentation.
- Adding more gesture classes.

## 👩‍💻 Project Context

This project was developed as part of a Machine Learning learning journey and training project with **TechTrek**.

## 📄 License

This project is intended for educational and learning purposes.
