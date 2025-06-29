# DDoS Detection with Decision Trees

## Overview
This project implements a **Decision Tree-based model** using a RandomForestClassifier to detect Distributed Denial of Service (DDoS) attacks in network traffic data. The model distinguishes between **DDoS** and **Benign** network activities using a subset of features from a large dataset.

The notebook (`Intrusion_Detection_Binary.ipynb`) processes a combined dataset from public sources (CIC DoS, CIC-IDS 2017, and CSE-CIC-IDS 2018) to classify network traffic as either DDoS or Benign.

## Dataset
- **Source**: [DDoS Balanced & Unbalanced Datasets](https://www.kaggle.com/datasets/devendra416/ddos-datasets) on Kaggle.
- **Description**: The dataset contains 84 features and over 12 million records, combining data from CIC DoS, CIC-IDS 2017, and CSE-CIC-IDS 2018. It focuses on binary classification (DDoS vs. Benign) rather than specific attack types.
- **Selected Features**:
  - Fwd Pkt Len Max
  - TotLen Fwd Pkts
  - ACK Flag Cnt
  - SYN Flag Cnt
  - Flow Duration
  - Tot Fwd Pkts
  - Bwd Pkt Len Max
  - Tot Bwd Pkts
  - RST Flag Cnt
  - Fwd Pkts/s
  - Init Fwd Win Byts
  - Label (DDoS or Benign)

## Prerequisites
To run the notebook, you need the following Python libraries:
- `pandas`
- `scikit-learn` (for RandomForestClassifier)
- `matplotlib` (for visualization)

You can install them using:
```bash
pip install pandas scikit-learn matplotlib
```

## Usage
1. **Download the Dataset**:
   - Obtain the dataset from [Kaggle](https://www.kaggle.com/datasets/devendra416/ddos-datasets).
   - Place the `final_dataset.csv` file in the same directory as the notebook.

2. **Run the Notebook**:
   - Open `Intrusion_Detection_Binary.ipynb` in Jupyter Notebook or any compatible environment.
   - Execute the cells sequentially to:
     - Load and preprocess the dataset (selecting relevant features and removing duplicates).
     - Train a RandomForestClassifier model.
     - Evaluate the model using a confusion matrix, classification report, and accuracy scores.
     - Analyze feature importance.

3. **Key Steps in the Notebook**:
   - **Data Loading**: Reads the dataset with selected features to manage its large size (>12M records).
   - **Preprocessing**: Removes duplicate entries (5,676,719 duplicates removed) and converts the `Label` column to numerical values (0 for Benign, 1 for DDoS).
   - **Model Training**: Uses RandomForestClassifier for binary classification.
   - **Evaluation**: Displays a confusion matrix, classification report (precision, recall, F1-score), and train/test accuracy.
   - **Feature Importance**: Lists the importance of each feature in the model.

## Results
- **Model Performance**:
  - **Train Accuracy**: ~99.63%
  - **Test Accuracy**: ~99.63%
  - **Classification Report**:
    - Precision: 0.99920 (Benign), 0.99290 (DDoS)
    - Recall: 0.99394 (Benign), 0.99906 (DDoS)
    - F1-Score: 0.99656 (Benign), 0.99597 (DDoS)
    - Overall Accuracy: 0.99629
  - **Confusion Matrix**:
    - The confusion matrix evaluates the model's performance on the test set (1,423,582 samples):
      - **True Negatives (Benign correctly classified)**: High accuracy in identifying Benign traffic (770,333 samples).
      - **True Positives (DDoS correctly classified)**: High accuracy in identifying DDoS traffic (653,249 samples).
      - **False Positives/Negatives**: Minimal misclassifications, indicating robust model performance (specific counts not detailed in the notebook but reflected in high precision/recall).
    - The matrix is visualized using a heatmap with `matplotlib`, highlighting the model's ability to correctly classify both classes with minimal errors.
  - **Key Features**: The most influential features include `Fwd Pkt Len Max` (21.86%), `Tot Fwd Pkts` (15.14%), and `TotLen Fwd Pkts` (13.88%).

## File Structure
- `Intrusion_Detection_Binary.ipynb`: The main Jupyter Notebook containing the code and analysis.
- `final_dataset.csv`: The dataset file (not included in the repository; download from Kaggle).
- `README.md`: This file, providing an overview and instructions.

## How to Contribute
Fork the repository.


## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Dataset provided by [Devendra416 on Kaggle](https://www.kaggle.com/datasets/devendra416/ddos-datasets).
