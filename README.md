# Workflow Anomaly Detection Using Machine Learning

## Overview

Anomaly detection plays a crucial role in identifying unusual patterns in workflow data and detecting potential system faults, security threats, and operational inefficiencies.

This project focuses on detecting anomalous workflow behavior using two different machine learning approaches:

1. **Unsupervised Learning Method** – Autoencoder Model
2. **Supervised/Hybrid Learning Method** – Rule-based + LLM/Classifiers

The system analyzes workflow execution records containing API calls, latency, response size, timestamps, and workflow patterns to identify abnormal behaviors.

---

# Introduction

## Background

Anomaly detection is widely used in domains such as:

- Healthcare
- Finance
- Cybersecurity
- System Monitoring

In workflow systems, anomalies may indicate:

- System failures
- Workflow inefficiencies
- Malicious activities

Traditional manual monitoring methods are no longer sufficient for modern large-scale systems. Machine learning enables automated and intelligent anomaly detection with improved accuracy and scalability.

---

## Motivation

Traditional rule-based systems struggle to detect:

- Unknown anomalies
- Evolving abnormal patterns
- Complex high-dimensional workflow behaviors

This project aims to build intelligent machine learning systems capable of learning normal workflow behavior and automatically detecting deviations.

---

## Objectives

The main objectives of this project are:

- Develop a workflow anomaly detection system
- Implement an Autoencoder-based unsupervised approach
- Implement a supervised/hybrid anomaly detection approach
- Compare performance of both approaches
- Analyze advantages and limitations of each method

---

## Scope of the Project

This project focuses on anomaly detection in structured workflow datasets using machine learning techniques.

### Scope Includes:
- Workflow preprocessing
- Feature engineering
- Unsupervised anomaly detection
- Supervised anomaly detection
- Performance evaluation

### Limitations:
- No real-time deployment
- Requires preprocessed datasets

---

# Literature Review

Traditional anomaly detection techniques include:

- Statistical methods
- Threshold-based systems
- Rule-based systems

However, these methods struggle with:

- Complex datasets
- High-dimensional workflow data
- Unknown anomaly patterns

Recent machine learning approaches include:

- Clustering techniques
- Classification models
- Deep learning methods
- Autoencoders

Autoencoders are highly effective because they learn compressed representations of normal workflow behavior without requiring labeled anomaly data.

Supervised methods such as:

- Decision Trees
- Support Vector Machines (SVM)
- Neural Networks

perform well when labeled data is available.

This project combines both supervised and unsupervised approaches to improve anomaly detection performance.

---

# System Overview

## Problem Definition

The goal of this project is to identify abnormal workflow execution patterns from workflow datasets containing API execution logs.

A workflow consists of:
- API calls
- Latency
- Response size
- Execution timestamps

Challenges include:
- Detecting anomalies without labels
- Identifying structural deviations
- Detecting timing abnormalities
- Detecting performance inconsistencies

---

# System Architecture

The system consists of the following stages:

1. Data Collection
2. Data Preprocessing
3. Feature Extraction
4. Model Training
5. Anomaly Detection
6. Performance Evaluation
7. Result Visualization

---

# Workflow

## Step-by-Step Workflow

### 1. Data Collection
Workflow execution records are collected.

### 2. Data Preprocessing
Data is cleaned and normalized.

### 3. Feature Engineering
Workflow-level features are extracted.

### 4. Model Training
Two methods are trained:

- Autoencoder-based model
- Hybrid Rule-based + LLM model

### 5. Anomaly Detection
Models identify abnormal workflow patterns.

### 6. Visualization
Results are visualized for interpretation and evaluation.

---

# Dataset and Preprocessing

## Dataset Description

The dataset contains execution records from a distributed API workflow system.

### Each record contains:
- Workflow ID
- API Name
- Start Timestamp
- End Timestamp
- Latency
- Response Size

### Dataset Split
- Training Dataset
- Testing Dataset

---

## Dataset Characteristics

| Characteristic | Value |
|---|---|
| Total Instances | ~14,000 |
| Raw Features | 6 |
| Processed Features | 8–12 |
| Numerical Features | 4 |
| Categorical Features | 1 |
| Missing Values | None |
| Observation Type | API-level Workflow Logs |

---

# Preprocessing Pipeline

## Data Cleaning

Validation checks performed:
- Missing values
- Duplicate entries
- Timestamp consistency
- Latency validation

Latency formula:

\[
latency = end - start
\]

---

## Feature Selection

Selected features:
- Latency
- Response Size
- API Name
- Start/End Timestamps

Workflow IDs are used only for grouping workflows.

---

## Feature Engineering

Workflow-level feature vectors include:
- Latency
- Response Size
- API Gap Time

This enables learning complete workflow behavior instead of individual API behavior.

---

## Feature Normalization

Z-score normalization used:

\[
x' = \frac{x - \mu}{\sigma}
\]

Where:
- \( \mu \) = Mean
- \( \sigma \) = Standard deviation

---

## Categorical Encoding

API names are converted into numerical representations using:
- One-Hot Encoding

---

## Class Balancing

SMOTE (Synthetic Minority Oversampling Technique) is used to handle imbalanced datasets.

---

# Method  – Autoencoder Model

## Overview

Method uses an Autoencoder neural network to learn normal workflow behavior.

The model reconstructs workflow inputs and calculates reconstruction error.

Higher reconstruction error indicates anomalies.

---

# Data Representation

Workflow feature vector:

\[
[L_1, L_2, ..., L_n, R_1, R_2, ..., R_n, G_1, G_2, ..., G_{n-1}]
\]

Where:
- \(L_i\) = API latency
- \(R_i\) = Response size
- \(G_i\) = Gap between API calls

---

# Feature Scaling

Robust Scaling is used:

\[
x' = \frac{x - median}{IQR}
\]

Where:
- IQR = Interquartile Range

This reduces the impact of outliers.

---

# Autoencoder Architecture

The Autoencoder contains:

- Input Layer
- Hidden Layer (32 neurons)
- Hidden Layer (16 neurons)
- Bottleneck Layer (8 neurons)
- Decoder Layer

The bottleneck layer learns compressed workflow representations.

---

# Model Training

## Training Parameters

| Parameter | Value |
|---|---|
| Loss Function | MSE |
| Optimizer | Adam |
| Batch Size | 64 |
| Epochs | Up to 200 |

### Early Stopping
Training stops if:
- No improvement for 10 consecutive epochs

---

# Reconstruction Error

MSE Reconstruction Error:

\[
MSE = \frac{1}{n}\sum_{i=1}^{n}(x_i - \hat{x_i})^2
\]

Where:
- \(x_i\) = Original feature
- \(\hat{x_i}\) = Reconstructed feature

Higher error indicates anomalies.

---

# Advantages

- No labeled anomaly data required
- Detects unknown anomalies
- Learns workflow-level behavior
- Feature-level explainability
- Resistant to outliers

---

# Limitations

- Sensitive to anomaly threshold selection
- Requires fixed-length feature vectors
- Performance depends on training quality

---

# Technologies Used

- Python
- TensorFlow / Keras
- Scikit-learn
- Pandas
- NumPy
- Matplotlib

---

# Future Improvements

- Real-time anomaly detection
- Adaptive thresholding
- Transformer-based workflow modeling
- Online learning systems
- Cloud deployment

---

# Conclusion

This project demonstrates the effectiveness of machine learning techniques for workflow anomaly detection using both supervised and unsupervised approaches.

The Autoencoder model successfully learns normal workflow behavior and identifies anomalies using reconstruction errors, while the hybrid supervised method enhances explainability and classification performance.

---

# Author

-Ashwika
-Geethika
-Diya

---
