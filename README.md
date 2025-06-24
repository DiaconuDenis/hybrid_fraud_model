# hybrid_fraud_model
Project Overview
This project presents a hybrid machine learning model designed for fraud detection, combining the strengths of Self-Organizing Maps (SOM) for unsupervised anomaly detection and Artificial Neural Networks (ANN) for supervised classification. The goal is to leverage SOM's ability to identify patterns and potential outliers in high-dimensional data, passing these insights to an ANN for a robust and accurate final fraud classification.

This innovative approach aims to enhance the precision and recall in detecting fraudulent activities, which is critical in various domains like financial transactions, insurance claims, and cybersecurity.

Why a Hybrid Approach?
Traditional fraud detection often relies solely on supervised learning, which can struggle with imbalanced datasets and evolving fraud patterns. A hybrid SOM-ANN model offers several advantages:

SOM as a Pre-processing/Anomaly Detection Layer:

Dimensionality Reduction & Visualization: SOMs project high-dimensional data onto a low-dimensional (e.g., 2D) grid, allowing for the visualization of data clusters and the identification of unusual data points (potential anomalies) that deviate from established patterns.
Unsupervised Anomaly Flagging: By mapping transactions to "Best Matching Units" (BMUs) and analyzing distances from these units, SOMs can flag transactions that are distant from normal behavior clusters, acting as an initial filter for suspicious activities.
ANN as a Refined Classifier:

Supervised Classification: The ANN takes the original features combined with insights derived from the SOM (e.g., BMU index, quantization error, or distance to closest cluster) to perform a final binary classification (fraud/non-fraud).
Pattern Recognition & Non-linear Relationships: ANNs excel at learning complex, non-linear relationships within data, allowing them to make nuanced decisions and reduce false positives/negatives based on the combined feature set.
Model Architecture and Workflow
The hybrid model operates in a sequential manner:

Data Pre-processing: Raw transaction data undergoes initial cleaning, feature engineering, and scaling.
SOM Training: The pre-processed data is fed into the SOM. The SOM learns to organize the data into clusters based on similarity.
Feature Augmentation from SOM: For each transaction, new features are generated based on its interaction with the trained SOM. Common features include:
The index of the Best Matching Unit (BMU).
The quantization error (distance from the input vector to its BMU), indicating how well the data point fits into the learned map.
BMU density or neighboring BMU information.
ANN Training: The original features, combined with the new SOM-derived features, form the input for the Artificial Neural Network. The ANN is then trained on labeled data (fraud/non-fraud) to learn the patterns indicative of fraud.
Prediction: During inference, new transactions follow the same path: SOM processing, feature augmentation, and then classification by the trained ANN.
