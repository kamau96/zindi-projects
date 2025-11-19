# Rainfall Prediction Using Indigenous Knowledge

This project builds an XGBoost classifier to predict rainfall intensity  
(**No Rain**, **Small Rain**, **Medium Rain**, **Heavy Rain**) using  
features derived from Indigenous Knowledge (IK) alongside basic numerical variables.

The main objective is to evaluate how useful community-based environmental indicators —
such as plant cues, animal behavior, and local observations — are when combined with
simple numerical/contextual features.

---

## 🌍 Dataset

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
- `rainfall_level`  
  (four classes: No Rain, Small Rain, Medium Rain, Heavy Rain)

### ⚠️ Note on Imbalance  
The dataset is imbalanced, but *no* class-weighting, oversampling, or SMOTE was applied.
The model is trained directly on the raw class distribution.

---

## 🧠 Modeling Approach (XGBoost Only)

This project intentionally focuses on **one algorithm**:  
➡️ **XGBoost (XGBClassifier)** for multi-class prediction.

### **Preprocessing Steps**
1. Split dataset into train/test with stratification.
2. Apply **one-hot encoding** on the listed categorical columns.
3. Concatenate with numeric features.
4. Train XGBoost using default or lightly tuned hyperparameters.
5. Evaluate using accuracy, macro F1, and confusion matrix.

No scaling was applied, as XGBoost does not require feature normalization.

---

## 📈 Evaluation

Key evaluation steps include:

- Stratified train/test split  
- Macro F1 to evaluate minority rainfall classes  
- Confusion matrix per class  
- Feature importance to understand which IK indicators contribute the most

Results vary by dataset version and cleaning steps, and will be updated as the project progresses.

---

## 📁 Project Structure

```markdown

rainfall-ik/
│
├── notebooks/
│   ├── 01-preprocessing.ipynb
│   ├── 02-training-xgboost.ipynb
│   └── 03-evaluation.ipynb
│
├── src/
│   ├── preprocess.py
│   ├── train_xgb.py
│   └── utils.py
│
├── data/          # (optional; usually excluded via .gitignore)
├── models/
├── README.md
└── requirements.txt
```


---

## 🚀 How to Run

1. Clone the repo  
   ```bash
   git clone https://github.com/<your-username>/rainfall-ik.git
   cd rainfall-ik
````

2. Install dependencies

   ```bash
   pip install -r requirements.txt
   ```

3. Open the notebooks

   ```bash
   jupyter notebook
   ```

---

## 🔮 Future Improvements

* Experiment with class-balancing strategies
* Compare XGBoost with LightGBM or CatBoost
* Introduce temporal features (lags, trends)
* Perform SHAP analysis for interpretability
* Build a simple inference script or web dashboard

---

## 📜 License

MIT License.

```

---

If you want, I can also generate:

✅ `requirements.txt`  
✅ `.gitignore` for a clean ML project  
✅ The project’s GitHub description text  
Just tell me!
```
