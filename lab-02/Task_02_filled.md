# Lab Task 02 — Effect of Image Filtering on Skin-Lesion Classification

## 1. Best three pretrained models (from Lab Activity 1)

**Best Model 1: VGG19 | Best Model 2: AlexNet | Best Model 3: ResNet101**

## 2. Comparison table

| Model | Filter | Accuracy | Precision | Recall | F1-score | Macro-F1 | Balanced Accuracy | AUC |
|---|---|---|---|---|---|---|---|---|
| VGG19 | No Filter | 46.56 | 47.36 | 46.84 | 43.50 | 43.50 | 46.84 | 82.00 |
| VGG19 | Average | 51.85 | 47.66 | 52.33 | 48.93 | 48.93 | 52.33 | 84.94 |
| VGG19 | Gaussian | 46.03 | 42.09 | 45.64 | 41.66 | 41.66 | 45.64 | 82.70 |
| VGG19 | Median | 50.26 | 37.14 | 48.53 | 42.00 | 42.00 | 48.53 | 85.07 |
| VGG19 | Sharpening | 44.97 | 38.17 | 43.42 | 40.20 | 40.20 | 43.42 | 84.14 |
| VGG19 | Sobel | 22.22 | 27.47 | 22.11 | 20.29 | 20.29 | 22.11 | 72.07 |
| AlexNet | No Filter | 53.44 | 55.05 | 51.06 | 49.29 | 49.29 | 51.06 | 86.25 |
| AlexNet | Average | 52.38 | 64.99 | 50.83 | 49.00 | 49.00 | 50.83 | 86.26 |
| AlexNet | Gaussian | 49.74 | 59.23 | 48.80 | 47.32 | 47.32 | 48.80 | 85.76 |
| AlexNet | Median | 52.91 | 68.89 | 50.75 | 48.83 | 48.83 | 50.75 | 87.18 |
| AlexNet | Sharpening | 48.68 | 58.40 | 46.94 | 44.61 | 44.61 | 46.94 | 85.60 |
| AlexNet | Sobel | 24.34 | 35.78 | 22.60 | 17.00 | 17.00 | 22.60 | 72.70 |
| ResNet101 | No Filter | 48.15 | 50.96 | 45.93 | 43.50 | 43.50 | 45.93 | 80.97 |
| ResNet101 | Average | 47.09 | 42.40 | 43.94 | 40.99 | 40.99 | 43.94 | 83.31 |
| ResNet101 | Gaussian | 47.62 | 44.18 | 44.94 | 43.55 | 43.55 | 44.94 | 84.36 |
| ResNet101 | Median | 45.50 | 52.18 | 42.68 | 42.20 | 42.20 | 42.68 | 81.59 |
| ResNet101 | Sharpening | 42.86 | 45.21 | 41.17 | 40.52 | 40.52 | 41.17 | 81.67 |
| ResNet101 | Sobel | 20.11 | 21.92 | 18.96 | 14.40 | 14.40 | 18.96 | 58.85 |

## 3. Figures

**HAM10000 class distribution**

![HAM10000 class distribution](Task_02_report_images/class_distribution.png)

**Original vs. filtered example image**

![Original vs. filtered example image](Task_02_report_images/filter_examples.png)

**Confusion matrices — 3 models x 6 filters**

![Confusion matrices — 3 models x 6 filters](Task_02_report_images/confusion_matrices.png)

**Test accuracy by filter, per model**

![Test accuracy by filter, per model](Task_02_report_images/accuracy_by_filter.png)

**Change in accuracy vs. baseline, per model**

![Change in accuracy vs. baseline, per model](Task_02_report_images/delta_accuracy_by_filter.png)
