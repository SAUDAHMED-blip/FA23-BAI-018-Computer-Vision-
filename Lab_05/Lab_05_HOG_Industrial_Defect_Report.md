# Lab 05: HOG-Based Industrial Defect Detection and Classification

## 1. Introduction

This experiment applies Histogram of Oriented Gradients (HOG) features
for industrial surface defect detection and classification.

The system follows the pipeline:

Image → Preprocessing → HOG Feature Extraction →
Machine Learning Classifier → Defective/Non-Defective Decision

---

## 2. Industrial Application

The proposed system can be used in industrial quality control to
automatically inspect manufactured surfaces and identify defective
products.

---

## 3. Dataset Description

Dataset:
NEU Surface Defect Database (NEU-DET)

Training Images Used:
1200

Validation Images Used:
100

Classes:
crazing, inclusion, patches, pitted_surface, rolled_in_scale, scratches

---

## 4. Image Preprocessing

Images were:

1. Resized to 128 × 128 pixels.
2. Converted to grayscale.
3. Normalized to the range 0–1.

---

## 5. HOG Feature Extraction

HOG parameters were investigated using:

- Cell sizes: 4×4, 8×8, 16×16
- Orientations: 6, 9, 12
- Cells per block: 2×2
- Block normalization: L2-Hys

Best configuration:

Cell Size: 16×16

Orientations: 12

Tuning Accuracy: 0.7222

Tuning F1 Score: 0.7167

---

## 6. Classification Methodology

Two machine-learning classifiers were evaluated:

1. Linear SVM
2. Random Forest

---

## 7. Classifier Results

### HOG + SVM

Accuracy: 0.7400

F1 Score: 0.7343

### HOG + Random Forest

Accuracy: 0.8800

F1 Score: 0.8786

### Best Classifier

HOG + Random Forest

---

## 8. HOG Parameter Experiment

Cell Size  Orientations  Accuracy  F1 Score  Features
    16x16            12  0.722222  0.716666      2352
      4x4             9  0.633333  0.621206     34596
    16x16             9  0.611111  0.599066      1764
      4x4             6  0.600000  0.583641     23064
      8x8             6  0.611111  0.562573      5400
    16x16             6  0.566667  0.556591      1176
      4x4            12  0.588889  0.554995     46128
      8x8             9  0.577778  0.550492      8100
      8x8            12  0.555556  0.528189     10800

---

## 9. Robustness Analysis

           Condition  Accuracy  F1 Score  Accuracy Change  F1 Change
Brightness Variation      0.63  0.622882            -0.11  -0.111401
      Gaussian Noise      0.21  0.126667            -0.53  -0.607616
            Rotation      0.31  0.254408            -0.43  -0.479875
                Blur      0.43  0.391254            -0.31  -0.343029

The robustness experiment investigated brightness variation,
Gaussian noise, rotation, and blur.

---

## 10. Industrial Deployment Discussion

The system can support automated industrial quality inspection.
A predicted defective product can be rejected while a non-defective
product can be accepted.

The final decision module produces:

- Prediction
- Confidence
- Recommended industrial action

---

## 11. Limitations

1. Performance depends on image quality.
2. Lighting changes can affect HOG features.
3. Noise and blur can reduce classification performance.
4. HOG primarily captures shape and edge information.
5. A larger and more diverse dataset may improve generalization.

---

## 12. Conclusion

HOG features were successfully applied to industrial surface images.
Different HOG cell sizes and orientation settings were compared.
SVM and Random Forest classifiers were trained and evaluated.

The system demonstrates how traditional computer vision and machine
learning can be combined for industrial quality control.

---

Report generated:
2026-10-08 05:12:08
