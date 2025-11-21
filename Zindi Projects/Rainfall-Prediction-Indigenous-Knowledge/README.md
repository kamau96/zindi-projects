# Rainfall Prediction Using Indigenous Knowledge

This project builds an XGBoost classifier to predict rainfall intensity  
(**No Rain**, **Small Rain**, **Medium Rain**, **Heavy Rain**) using  
features derived from Indigenous Knowledge (IK) alongside basic numerical variables.

The main objective is to evaluate how effective community-based environmental indicators —
such as plant cues, animal behavior, and local observations — are when incorporated into model machine learning models.

---
## 📁 Project Structure

```markdown

rainfall-prediction-indigenous-knowledge/
│
├── notebooks/
│   ├── ghana-s-indigenous-challenge-final-solution.ipynb
│   └── ghana-s-indigenous-intel-challenge-eda.ipynb.ipynb
│
├── documentation.pdf
├── README.md
└── requirements.txt
```

---
## 🚀 How to Run

1. Clone the repo  
   ```bash
   git clone https://github.com/<your-username>/rainfall-prediction-indigenous-knowledge.git
   cd rainfall-prediction-indigenous-knowledge
   ```

2. Install dependencies 

   ```bash
   pip install -r requirements.txt
   ```

3. Open the notebooks

   ```bash
   jupyter notebook
   ```
If running ghana-s-indigenous-challenge-final-solution notebook on kaggle or colab, just uncomment the first and second code blocks. Ensure that paths to the files are correctly defined. 

---
## 🌍 Dataset

The dataset can be download from the following page [....]
After initial cleaning, the dataset includes the following usable columns:

### **🔥 One-hot encoded categorical columns**
- `community`
- `district`
- `indicator`
- `pred_date`

### **🔢 Numeric/continuous columns used as-is**
- `user_id`
- `predicted_intensity`
- `confidence`
- `forecast_length`
- `month`
- `day`
- `hour`
- `dow`

Columns such as **`time_observed`** and **`indicator_description`** were dropped during preprocessing.

### 🏷️ Target variable
- `Target`  
  (four classes: No Rain, Small Rain, Medium Rain, Heavy Rain)

### ⚠️ Note on Imbalance  
The dataset is imbalanced, but *no* class-weighting, oversampling, or SMOTE was applied.
The model is trained directly on the raw class distribution.

---
## 🧠 Modeling Approach (XGBoost Only)

This project intentionally focuses on **one algorithm**:  
➡️ **XGBoost (XGBClassifier)** for multi-class prediction.

### **Preprocessing Steps**
1. Split dataset into train/validation with stratification.
2. Apply **one-hot encoding** on the listed categorical columns.
3. Concatenate with numeric features.
4. Train XGBoost using lightly tuned hyperparameters.
5. Evaluate using macro F1.

No scaling was applied, as XGBoost does not require feature normalization.

---
## 📈 Evaluation

Key evaluation steps include:

- OOF predictions  
- Macro F1 to evaluate minority rainfall classes  
- Feature importance to understand which IK indicators contribute the most (SHAP)

---
## 🔮 Future Improvements

* Experiment with class-balancing strategies (already attempted)
* Compare XGBoost with LightGBM or CatBoost (already attempted)
* Introduce temporal features (lags, trends)
* Build a simple inference script or web dashboard

---
## 📜 License

MIT License.

---
