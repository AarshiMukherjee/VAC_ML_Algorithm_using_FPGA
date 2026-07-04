# Skin Cancer Classification using Transfer Learning, Attention Mechanism, and FPGA-Oriented Model Compression

## Overview

This project implements **skin lesion classification system** using deep learning. It utilizes a pretrained **VGG16** convolutional neural network as the feature extractor and explores multiple stages of model optimization for efficient deployment.

The project consists of:

- Transfer Learning using VGG16
- Attention Mechanism
- Skin lesion classification
- Model evaluation using multiple performance metrics
- Extraction of trained classifier weights
- Weight pruning
- Weight sharing analysis
- Fixed-point conversion for FPGA deployment

The final objective is to reduce computational complexity and memory requirements while maintaining classification performance, making the model suitable for hardware implementations.

---

## Features

- Pretrained VGG16 backbone (ImageNet weights)
- Data augmentation
- Custom attention module
- Confusion Matrix
- Classification Report
- ROC Curve & AUC Score
- Automatic extraction of Dense layer weights
- Weight pruning
- Weight sharing analysis
- Manual fixed-point binary conversion
- FPGA-friendly optimization pipeline

---

## Project Workflow

```
Dataset
   │
   ▼
Data Augmentation
   │
   ▼
Pretrained VGG16
   │
   ▼
Attention Module
   │
   ▼
Classifier
   │
   ▼
Performance Evaluation
   │
   ▼
Extract Dense Weights
   │
   ▼
Weight Pruning
   │
   ▼
Weight Sharing Analysis
   │
   ▼
Fixed Point Conversion
   │
   ▼
FPGA Deployment Preparation
```

---

## Model Architecture

### Baseline Model

- VGG16 (Frozen Feature Extractor)
- Flatten Layer
- Dense (256)
- Dropout (0.5)
- Dense (2, Softmax)

---

### Proposed Model

The improved architecture introduces an attention mechanism.

#### Channel Attention

- Global Max Pooling
- Global Average Pooling
- Feature Concatenation
- Dense Layer
- Feature Reweighting

#### Spatial Attention

- Average Pooling
- Max Pooling
- Concatenation
- Batch Normalization
- 1×1 Convolution
- Dense Layer
- Spatial Feature Reweighting

The outputs from both attention branches are fused before the final classifier.

---

## Evaluation Metrics

The project evaluates performance using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC Curve
- Area Under Curve (AUC)

---

## Model Compression Pipeline

### 1. Weight Extraction

The trained Dense layers are exported to Excel files for analysis.

---

### 2. Weight Pruning

Weights are grouped into three regions:

- Positive Mean
- Zero
- Negative Mean

Small weights are removed by replacing them with zero.

Benefits:

- Reduced parameters
- Reduced computation
- Lower memory consumption

---

### 3. Weight Sharing

The pruned weights are analyzed to identify repeated values.

Repeated weights can share memory addresses, reducing storage requirements.

---

### 4. Fixed Point Conversion

The pruned weights are converted into manual **fixed-point binary representation**.

Advantages:

- FPGA compatibility
- Reduced hardware complexity
- Faster arithmetic
- Lower power consumption

---

## Technologies Used

- Python
- TensorFlow / Keras
- NumPy
- Pandas
- OpenCV
- Matplotlib
- Seaborn
- Scikit-learn

## Future Work

- FPGA implementation using Verilog/VHDL
- Mobile deployment
- Use of Explanable AI techniques for better diagnosis

---

## Applications

- Computer-aided skin cancer diagnosis
- Clinical decision support
---

