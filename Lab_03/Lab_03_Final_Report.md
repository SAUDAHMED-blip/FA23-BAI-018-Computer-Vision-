LAB 03
Edge Detection Techniques and Their Impact on Classification Performance

Computer Vision / Artificial Intelligence Laboratory
Skin Cancer Image Classification Dataset
Six Selected Classes

# 1. Objectives
Understand the concept of edge detection in digital images.
Implement Sobel, Prewitt, Laplacian, LoG and Canny edge detectors.
Study the effect of Gaussian and Salt-and-Pepper noise on edge detection.
Study the effect of Gaussian and Median filtering.
Analyze different Canny threshold configurations.
Compare raw, filtered and edge-based image classification.
Evaluate classification using accuracy, precision, recall and F1-score.
Analyze confusion matrices and classification performance.
# 2. Dataset and Experimental Setup
The experiment uses the ISIC skin cancer image dataset. Six classes were selected for the laboratory experiment.
## Selected Classes

# 3. Task 1 - Comparative Edge Detection
Different classical edge detection techniques were applied to representative skin images. The techniques include Sobel, Prewitt, Laplacian, LoG and Canny.

Figure 1. Comparative edge detection results.
# 4. Task 2 - Noise and Preprocessing Analysis
Gaussian noise and Salt-and-Pepper noise were introduced to investigate their effect on edge detection. Gaussian filtering and Median filtering were then applied.
## Table 1 - Noise and Preprocessing Effect on Edge Detection

Figure 2. Noise and preprocessing examples.
# 5. Task 3 - Canny Parameter Analysis
Different Canny threshold configurations were tested to observe their effect on the detected edge map.
## Table 2 - Canny Parameter Analysis

Figure 3. Canny edge detection with different thresholds.
# 6. Task 4 - Classification Using Different Representations
Three image representations were compared using the same classification framework: Raw images, Filtered images, and Edge images.
Set A: Raw Images
Set B: Filtered Images
Set C: Edge Images
# 7. Task 5 - Classification Performance
## Table 3 - Classification Performance

# 8. Raw vs Filtered vs Edge Classification
## Classification Metric Comparison

Figure 4. Comparison of classification performance.
# 9. Task 6 - Confusion Matrix Analysis
Confusion matrices were generated for Raw, Filtered and Edge image representations.

Figure 5. Confusion matrix for raw images.

Figure 6. Confusion matrix for filtered images.

Figure 7. Confusion matrix for edge images.
# 10. Discussion
Effect of Noise: Noise introduces unwanted intensity variations that can produce additional or irregular edges. Therefore, edge detectors can become more sensitive to noisy images.
Effect of Filtering: Gaussian filtering reduces high-frequency noise and can make edge detection more stable. Median filtering is particularly useful for Salt-and-Pepper noise.
Canny Thresholds: Changing the low and high thresholds changes the number and strength of detected edges. Lower thresholds may detect more edges, while higher thresholds generally produce a more selective edge map.
Classification: Raw images contain color, texture and structural information. Edge images emphasize boundaries and shape information but may remove other information useful for classification.
CNN Features: CNNs can learn low-level features such as edges directly from raw images. Therefore, explicit edge preprocessing does not necessarily improve classification performance.
# 11. Experimental Result Summary
Raw-image accuracy: 0.5395
Filtered-image accuracy: 0.5704
Edge-image accuracy: 0.2955
Raw-image F1-score: 0.5137
Filtered-image F1-score: 0.5366
Edge-image F1-score: 0.2735
# 12. Conclusion
This laboratory experiment demonstrated the application of classical edge detection techniques including Sobel, Prewitt, Laplacian, LoG and Canny on skin cancer images. The experiment also examined the effect of Gaussian and Salt-and-Pepper noise and the role of Gaussian and Median filtering.
Different Canny threshold configurations were compared to observe their effect on edge maps. Finally, raw, filtered and edge-based image representations were evaluated using a CNN classification framework.
The experimental results, tables, confusion matrices and performance comparison provide a basis for understanding how image preprocessing and edge information affect classification performance.
# 13. Viva Preparation Questions
1. What is edge detection?
2. What is the difference between first-order and second-order edge detectors?
3. What are Sobel Gx and Gy?
4. Why is the Laplacian sensitive to noise?
5. Why is Gaussian smoothing used before edge detection?
6. What is the main advantage of the Canny edge detector?
7. What are the low and high thresholds in Canny?
8. What is the difference between Gaussian noise and Salt-and-Pepper noise?
9. Why is Median filtering useful for Salt-and-Pepper noise?
10. Why can edge-based classification perform worse than raw-image classification?
11. Can CNNs learn edge features automatically?
12. Why might raw images contain more useful information than edge images?
# 14. Generated Result Files
Classification_Comparison.png
Confusion_Matrix_Edge.png
Confusion_Matrix_Filtered.png
Confusion_Matrix_Raw.png
Task_1_Edge_Detection.png
Task_2_Noise_Preprocessing.png
Task_3_Canny_Analysis.png

| Class ID | Class Name |
| --- | --- |
| 0 | actinic keratosis |
| 1 | basal cell carcinoma |
| 2 | dermatofibroma |
| 3 | melanoma |
| 4 | nevus |
| 5 | pigmented benign keratosis |

| Detector | Input Image | Preprocessing | Detected Edge Pixels | Edge Percentage (%) |
| --- | --- | --- | --- | --- |
| Sobel | Original | None | 1565 | 6.11 |
| Sobel | Gaussian Noise | None | 8052 | 31.45 |
| Sobel | Salt & Pepper Noise | None | 5934 | 23.18 |
| Sobel | Gaussian Noise | Gaussian Filter | 3208 | 12.53 |
| Sobel | Salt & Pepper Noise | Median Filter | 1200 | 4.69 |
| Prewitt | Original | None | 1521 | 5.94 |
| Laplacian | Original | None | 432 | 1.69 |
| LoG | Gaussian Noise | Gaussian Filter | 9263 | 36.18 |
| Canny | Original | Built-in Gaussian Smoothing | 865 | 3.38 |
| Canny | Gaussian Noise | Gaussian Filter | 211 | 0.82 |
| Canny | Salt & Pepper Noise | Median Filter | 306 | 1.2 |

| Configuration | Low Threshold | High Threshold | Kernel Size | Detected Edge Pixels | Edge Percentage (%) |
| --- | --- | --- | --- | --- | --- |
| Canny-1 | 30 | 100 | 3 | 1011 | 3.95 |
| Canny-2 | 50 | 150 | 3 | 358 | 1.4 |
| Canny-3 | 100 | 200 | 3 | 111 | 0.43 |
| Canny-4 | 50 | 150 | 5 | 251 | 0.98 |

| Model | Accuracy Raw | Accuracy Filtered | Accuracy Edge | Precision Raw | Recall Raw | F1 Raw | Precision Filtered | Recall Filtered | F1 Filtered | Precision Edge | Recall Edge | F1 Edge | Training Time Raw (s) | Training Time Filtered (s) | Training Time Edge (s) | Inference Raw (ms) | Inference Filtered (ms) | Inference Edge (ms) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| CNN | 0.5395 | 0.5704 | 0.2955 | 0.5053 | 0.5395 | 0.5137 | 0.5179 | 0.5704 | 0.5366 | 0.2591 | 0.2955 | 0.2735 | 30.1075 | 23.902 | 15.5631 | 6.5959 | 9.7858 | 7.1412 |

| Representation | Accuracy | Precision | Recall | F1-Score |
| --- | --- | --- | --- | --- |
| Raw | 0.5395 | 0.5053 | 0.5395 | 0.5137 |
| Filtered | 0.5704 | 0.5179 | 0.5704 | 0.5366 |
| Edge | 0.2955 | 0.2591 | 0.2955 | 0.2735 |
