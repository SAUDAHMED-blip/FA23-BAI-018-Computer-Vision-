# Task 01 Results Summary

### Table 1. Comparison of Transfer Learning Models

| Model | Accuracy (%) | Precision (%) | Recall (%) | F1-Score (%) | AUC (%) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| AlexNet | 49.15 | 46.34 | 49.31 | 41.76 | 88.52 |
| VGG16 | 43.22 | 40.80 | 44.44 | 37.45 | 85.71 |
| VGG19 | 51.69 | 51.24 | 51.39 | 46.65 | 88.55 |
| ResNet18 | 37.29 | 27.36 | 39.58 | 28.22 | 83.72 |
| ResNet50 | 38.98 | 29.13 | 40.97 | 29.43 | 85.34 |
| ResNet101 | 44.07 | 48.83 | 45.14 | 36.96 | 85.71 |
| DenseNet121 | 34.75 | 31.82 | 34.49 | 28.21 | 81.62 |
| EfficientNet-B0 | 29.66 | 23.12 | 30.32 | 23.13 | 77.82 |

---

### Table 2. Comparison of Different Classifiers

| Feature Extractor | Classifier | Accuracy (%) | Precision (%) | Recall (%) | F1-Score (%) | AUC (%) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| Deep Features | Logistic Regression | 44.07 | 53.20 | 48.15 | 46.31 | 80.19 |
| Deep Features | Decision Tree | 33.90 | 28.39 | 36.81 | 29.16 | 64.20 |
| Deep Features | Random Forest | 48.31 | 50.55 | 48.61 | 42.53 | 88.40 |
| Deep Features | K-Nearest Neighbors (KNN) | 44.92 | 48.58 | 45.83 | 43.99 | 77.44 |
| Deep Features | Linear SVM | 44.07 | 53.30 | 48.15 | 45.82 | 86.83 |
| Deep Features | RBF-SVM | 36.44 | 42.46 | 32.87 | 30.51 | 82.04 |
| Deep Features | XGBoost | 45.76 | 43.44 | 46.53 | 41.22 | 88.49 |

---

### Table 3. Computational Efficiency Comparison

| Model | Parameters (M) | Model Size (MB) | FLOPs (G) | Inference Time (ms) | Accuracy (%) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| AlexNet | 57.04 | 228.17 | 0.71 | 2.1 | 49.15 |
| VGG16 | 134.3 | 537.2 | 15.47 | 10.81 | 43.22 |
| VGG19 | 139.61 | 558.44 | 19.63 | 12.33 | 51.69 |
| ResNet18 | 11.18 | 44.81 | 1.82 | 2.98 | 37.29 |
| ResNet50 | 23.53 | 94.43 | 4.13 | 8.15 | 38.98 |
| DenseNet121 | 6.96 | 28.5 | 2.9 | 15.82 | 34.75 |
| EfficientNet-B0 | 4.02 | 16.48 | 0.41 | 8.27 | 29.66 |