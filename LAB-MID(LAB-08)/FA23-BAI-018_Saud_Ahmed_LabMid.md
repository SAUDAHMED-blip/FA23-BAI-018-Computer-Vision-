
# Computer Vision Lab Mid Exam
## HOG vs SIFT on BloodMNIST

**Name:** Saud Ahmed  
**Registration:** FA23-BAI-018  
**Dataset:** BloodMNIST (MedMNIST, size 64)

## Q1 — Dataset setup

- Training images: (400, 128, 128)
- Validation images: (120, 128, 128)
- Test images: (120, 128, 128)
- Classes: Eosinophil, Monocyte, Neutrophil, Platelet
- Images per class: 100 training, 30 validation, 30 test
- Image preprocessing: grayscale and resize to 128 × 128
- Random seed: 18

The notebook displays four example images for each class.

## Q2 — HOG + SVM

HOG settings:
- Cell size: 8 × 8
- Orientations: 9
- Block size: 2 × 2 cells
- Normalization: L2-Hys

Feature calculation:

- Cells per dimension = 128 / 8 = 16
- Blocks per dimension = 16 - 2 + 1 = 15
- Values per block = 2 × 2 × 9 = 36
- Total features = 15 × 15 × 36 = **8,100**

Selected C: 0.1  
Validation accuracy: 0.7167  
Validation macro-F1: 0.7231

Confusion matrix (rows = actual; columns = predicted):

[[20  7  3  0]
 [ 8 21  1  0]
 [ 4  8 18  0]
 [ 1  2  0 27]]

## Q3 — SIFT + SVM

Normal SIFT keypoint statistics:

- Average keypoints: 71.92
- Minimum keypoints: 10
- Maximum keypoints: 187
- Images with zero keypoints: 0

Fixed-grid SIFT settings:

- Grid: 6 × 6
- Keypoints: 36
- Keypoint size: 32
- Descriptor length: 128
- Expected feature length: 36 × 128 = **4,608**

Selected C: 0.1  
Validation accuracy: 0.7667  
Validation macro-F1: 0.7678

Confusion matrix (rows = actual; columns = predicted):

[[17 11  2  0]
 [ 7 22  0  1]
 [ 3  2 24  1]
 [ 0  1  0 29]]

Normal SIFT can produce different numbers of descriptors for different
images. Fixed-length feature vectors are required for standard SVM input.

## Q4 — Robustness testing

The test set is used for final evaluation only. C was selected using
validation data.

### Actual results

     Model                 Condition  Accuracy  Macro-F1  Precision (macro)  Recall (macro)
 HOG + SVM                     Clean    0.7083    0.7113             0.7151          0.7083
 HOG + SVM        Rotated 20 degrees    0.7250    0.7281             0.7387          0.7250
 HOG + SVM Gaussian noise sigma=0.05    0.2500    0.1000             0.0625          0.2500
SIFT + SVM                     Clean    0.6833    0.6805             0.6865          0.6833
SIFT + SVM        Rotated 20 degrees    0.6833    0.6856             0.6924          0.6833
SIFT + SVM Gaussian noise sigma=0.05    0.6917    0.6844             0.6840          0.6917

### Model comparison

     Model  Selected C  Clean Accuracy  Clean Macro-F1  Rotated 20 degrees Accuracy  Rotated 20 degrees Macro-F1  Gaussian noise sigma=0.05 Accuracy  Gaussian noise sigma=0.05 Macro-F1
 HOG + SVM         0.1          0.7083          0.7113                       0.7250                       0.7281                              0.2500                              0.1000
SIFT + SVM         0.1          0.6833          0.6805                       0.6833                       0.6856                              0.6917                              0.6844

### Class-level metrics

     Model      Class  TP  TN  FP  FN  Precision  Recall  Specificity
 HOG + SVM Eosinophil  15  75  15  15     0.5000  0.5000       0.8333
 HOG + SVM   Monocyte  19  77  13  11     0.5938  0.6333       0.8556
 HOG + SVM Neutrophil  23  83   7   7     0.7667  0.7667       0.9222
 HOG + SVM   Platelet  28  90   0   2     1.0000  0.9333       1.0000
SIFT + SVM Eosinophil  16  72  18  14     0.4706  0.5333       0.8000
SIFT + SVM   Monocyte  15  83   7  15     0.6818  0.5000       0.9222
SIFT + SVM Neutrophil  21  79  11   9     0.6562  0.7000       0.8778
SIFT + SVM   Platelet  30  88   2   0     0.9375  1.0000       0.9778

The notebook's accuracy and macro-F1 graphs are included in the PDF
when their image files are available.

**Interpretation:** Compare clean, rotated 20-degree and Gaussian-noise
results. State whether the original prediction was supported by the
actual results; do not assume one method is better in advance.

## Q5 — Short answers

### (a) Why does HOG use block normalization?

Block normalization scales local gradient histograms, reducing sensitivity
to illumination and contrast changes. L2-Hys also limits the influence
of unusually large gradient values.

### (b) Why must C not be selected using the test set?

Selecting C on test data leaks information from the final evaluation set
into model selection and can bias the performance estimate. C must be
selected using validation data.

### (c) Which classes were confused most?

Use the clean-test confusion matrices in the notebook to identify the
largest off-diagonal entry for each model. Grayscale removes colour cues,
which can make visually similar blood-cell classes harder to distinguish.

### (d) AI log

| Prompt | Change | Check |
|---|---|---|
| Build the Q1-Q5 HOG/SIFT lab notebook | Applied registration-specific settings and fixed-grid SIFT | Checked feature lengths, plots, metrics and confusion matrices |

## Formulas

- Accuracy = (TP + TN) / (TP + TN + FP + FN)
- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- Specificity = TN / (TN + FP)
- F1 = 2 × Precision × Recall / (Precision + Recall)
- Macro-F1 = average of the per-class F1 scores

For multiclass classification, TP, TN, FP and FN are computed separately
for each class using a one-vs-rest approach.

## Conclusion

Compare HOG + SVM and SIFT + SVM using validation results and the three
test conditions. Base the final conclusion on the actual measured values,
not on the initial prediction.

**Reproducibility:** Results depend on the data subset, random seed,
library versions and execution environment.
