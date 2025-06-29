
# 🛡️ Binary Intrusion Detection using Decision Trees and Random Forests

This project implements a binary **Intrusion Detection System (IDS)** using classical machine learning models. It distinguishes between **Benign** and **DDoS** network traffic based on selected features from a specialized dataset.

---

## 📌 Objective

To develop and evaluate decision tree–based models (including Random Forests) for detecting **DDoS attacks** using a simplified, selected subset of features.

---

## 📂 Dataset

The dataset used is the [DDoS Balanced & Unbalanced Datasets](https://www.kaggle.com/datasets/devendra416/ddos-datasets), which contains features extracted from network traffic to identify malicious behavior.

- **Original Source**: Kaggle  
- **Composition**: Combined from multiple sources (CIC DoS, CI-CIDS 2017, CSE-CIC-IDS 2018)  
- **Label Classes**: 
  - `Benign`
  - `DDoS`

Only these two classes are used in this binary classification task.

---

## 🧠 Features Selected

Out of 80+ features, the following **12** were selected as most informative:

```text
'Fwd Pkt Len Max',
'TotLen Fwd Pkts',
'ACK Flag Cnt',
'SYN Flag Cnt',
'Flow Duration',
'Tot Fwd Pkts',
'Bwd Pkt Len Max',
'Tot Bwd Pkts',
'RST Flag Cnt',
'Fwd Pkts/s',
'Init Fwd Win Byts',
'Label'
```

---

## 🧼 Preprocessing Steps

1. **Feature Selection**: Only selected columns are loaded from CSV.  
2. **NaN Check**: Ensures no missing values exist.  
3. **Duplicate Removal**: Duplicate rows are removed.  
4. **Label Encoding**:

```python
df['Label'] = df['Label'].apply(lambda x: 0 if x == 'Benign' else 1)
```

- `0`: Benign  
- `1`: DDoS

5. **Train/Test Split**: 80/20 split with stratification for label balance.

---

## ⚙️ Models Used

Two classifiers from `scikit-learn` were implemented:

### 1. Decision Tree Classifier

- `criterion='entropy'`  
- `max_depth=9`

### 2. Random Forest Classifier

- `n_estimators=25`  
- `criterion='entropy'`  
- `max_depth=10`

---

## 📊 Evaluation Metrics

- **Accuracy**
- **Confusion Matrix**
- **Classification Report** (Precision, Recall, F1-Score)
- **Feature Importance**
- **Underfitting/Overfitting Analysis**

### Example Random Forest Results:

```text
Train Accuracy: 0.99985
Test  Accuracy: 0.99892
```
The model shows high performance in both training and test phases.

---

## 📈 Feature Importance (Top 5)

1. Flow Duration  
2. ACK Flag Count  
3. TotLen Fwd Pkts  
4. Fwd Pkt Len Max  
5. SYN Flag Count  


---

## 🤝 Contributing

Contributions are welcome! Please fork the repo and submit a pull request.

You can also open issues for:
- Dataset enhancement
- Feature engineering ideas
- Model improvement

---

## 📄 License

This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Kaggle DDoS Dataset](https://www.kaggle.com/datasets/devendra416/ddos-datasets)   
- CIC and CSE-CIC dataset providers

---
