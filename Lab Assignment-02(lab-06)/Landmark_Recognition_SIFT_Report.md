# Computer Vision Lab Assignment
## Landmark Recognition Using the SIFT Algorithm

**Report generated:** 2026-10-15 04:52:21

---

## 1. Objective
Develop a computer vision application that recognizes famous landmarks using SIFT feature extraction, Brute-Force descriptor matching, Lowe's ratio test, and RANSAC-based geometric verification.

## 2. Tools and Technologies
- Python
- Google Colab
- OpenCV
- SIFT (Scale-Invariant Feature Transform)
- Brute-Force Matcher with Euclidean (L2) distance
- K-nearest-neighbor matching (k=2)
- Lowe's ratio test
- Homography estimation using RANSAC
- NumPy, Pandas, Matplotlib
- Kaggle dataset

## 3. Dataset and Reference Database

- **Eiffel Tower:** 100 valid source images
- **Taj Mahal:** 100 valid source images
- **Great Wall of China:** 100 valid source images
- **Statue of Liberty:** 100 valid source images
- **Colosseum:** 100 valid source images

- Reference images prepared: 375
- Held-out test images prepared: 125

Reference images are organized into folders by landmark category.

## 4. Methodology

### 4.1 SIFT Feature Extraction
Each image is converted to grayscale. SIFT detects distinctive keypoints and calculates a descriptor vector for each keypoint.

### 4.2 Feature Matching
The Brute-Force Matcher compares SIFT descriptors using Euclidean distance. KNN matching retrieves two nearest neighbors, and Lowe's ratio test filters ambiguous matches.

### 4.3 Landmark Recognition
The system ranks reference images by reliable descriptor matches. A landmark is accepted only when the match count, RANSAC inlier count, and inlier ratio meet the configured thresholds.

### 4.4 Landmark Localization
Homography estimation with RANSAC checks geometric consistency between the reference image and query image. When the transformation passes the implemented checks, the projected reference-image corners are drawn as a polygon on the query image.

- Lowe ratio threshold: 0.75
- Minimum reliable matches: 12
- Minimum RANSAC inliers: 8
- Minimum inlier ratio: 0.35

## 5. Experimental Results

### 5.1 Individual Test Results

| condition          | true_landmark       | predicted_landmark   | best_candidate      |   query_keypoints |   reliable_matches |   ransac_inliers |   inlier_ratio | recognized   | correct_candidate   |   processing_time_sec |
|:-------------------|:--------------------|:---------------------|:--------------------|------------------:|-------------------:|-----------------:|---------------:|:-------------|:--------------------|----------------------:|
| Original           | Colosseum           | Colosseum            | Colosseum           |               521 |                183 |              147 |          0.803 | True         | True                |                7.9    |
| Rotated 25 degrees | Colosseum           | Colosseum            | Colosseum           |               435 |                170 |              138 |          0.812 | True         | True                |                6.4646 |
| Resized            | Colosseum           | Colosseum            | Colosseum           |               611 |                167 |              144 |          0.862 | True         | True                |                8.8549 |
| Reduced brightness | Colosseum           | Colosseum            | Colosseum           |               510 |                179 |              146 |          0.816 | True         | True                |                5.7494 |
| Original           | Colosseum           | Unknown              | Statue of Liberty   |              2501 |                146 |                4 |          0.027 | False        | False               |               27.7175 |
| Rotated 25 degrees | Colosseum           | Unknown              | Statue of Liberty   |              2500 |                124 |                5 |          0.04  | False        | False               |               27.407  |
| Resized            | Colosseum           | Unknown              | Statue of Liberty   |              2500 |                104 |                5 |          0.048 | False        | False               |               28.3224 |
| Reduced brightness | Colosseum           | Unknown              | Statue of Liberty   |              2266 |                145 |                6 |          0.041 | False        | False               |               25.0195 |
| Original           | Colosseum           | Colosseum            | Colosseum           |               442 |                 94 |               89 |          0.947 | True         | True                |                4.8867 |
| Rotated 25 degrees | Colosseum           | Colosseum            | Colosseum           |               590 |                110 |              106 |          0.964 | True         | True                |                7.2451 |
| Resized            | Colosseum           | Colosseum            | Colosseum           |               435 |                 61 |               57 |          0.934 | True         | True                |                4.7571 |
| Reduced brightness | Colosseum           | Colosseum            | Colosseum           |               254 |                 78 |               74 |          0.949 | True         | True                |                2.8451 |
| Original           | Colosseum           | Colosseum            | Colosseum           |              2500 |                201 |              187 |          0.93  | True         | True                |               27.6598 |
| Rotated 25 degrees | Colosseum           | Colosseum            | Colosseum           |              2500 |                188 |              167 |          0.888 | True         | True                |               27.5432 |
| Resized            | Colosseum           | Colosseum            | Colosseum           |              2500 |                364 |              352 |          0.967 | True         | True                |               27.6569 |
| Reduced brightness | Colosseum           | Colosseum            | Colosseum           |              2500 |                205 |              191 |          0.932 | True         | True                |               27.3373 |
| Original           | Colosseum           | Colosseum            | Colosseum           |               416 |                133 |              128 |          0.962 | True         | True                |                4.6026 |
| Rotated 25 degrees | Colosseum           | Colosseum            | Colosseum           |               508 |                147 |              140 |          0.952 | True         | True                |                5.5978 |
| Resized            | Colosseum           | Colosseum            | Colosseum           |               388 |                103 |               95 |          0.922 | True         | True                |                4.3571 |
| Reduced brightness | Colosseum           | Colosseum            | Colosseum           |               267 |                134 |              128 |          0.955 | True         | True                |                2.9461 |
| Original           | Eiffel Tower        | Eiffel Tower         | Eiffel Tower        |               399 |                161 |              158 |          0.981 | True         | True                |                4.4715 |
| Rotated 25 degrees | Eiffel Tower        | Eiffel Tower         | Eiffel Tower        |               436 |                158 |              151 |          0.956 | True         | True                |                4.765  |
| Resized            | Eiffel Tower        | Eiffel Tower         | Eiffel Tower        |               559 |                 89 |               87 |          0.978 | True         | True                |                6.2505 |
| Reduced brightness | Eiffel Tower        | Eiffel Tower         | Eiffel Tower        |               326 |                151 |              146 |          0.967 | True         | True                |                3.6806 |
| Original           | Eiffel Tower        | Eiffel Tower         | Eiffel Tower        |               220 |                 19 |                8 |          0.421 | True         | True                |                2.4492 |
| Rotated 25 degrees | Eiffel Tower        | Unknown              | Eiffel Tower        |               184 |                 17 |                7 |          0.412 | False        | True                |                2.1001 |
| Resized            | Eiffel Tower        | Unknown              | Taj Mahal           |               145 |                  9 |                0 |          0     | False        | False               |                1.7181 |
| Reduced brightness | Eiffel Tower        | Unknown              | Eiffel Tower        |               123 |                 11 |                7 |          0.636 | False        | True                |                1.3864 |
| Original           | Eiffel Tower        | Unknown              | Great Wall of China |               226 |                  8 |                5 |          0.625 | False        | False               |                2.5092 |
| Rotated 25 degrees | Eiffel Tower        | Unknown              | Eiffel Tower        |               308 |                  9 |                6 |          0.667 | False        | True                |                3.4018 |
| Resized            | Eiffel Tower        | Unknown              | Statue of Liberty   |               393 |                 13 |                4 |          0.308 | False        | False               |                4.4228 |
| Reduced brightness | Eiffel Tower        | Unknown              | Great Wall of China |               163 |                  8 |                5 |          0.625 | False        | False               |                1.8211 |
| Original           | Eiffel Tower        | Unknown              | Great Wall of China |               286 |                 16 |                5 |          0.312 | False        | False               |                3.1499 |
| Rotated 25 degrees | Eiffel Tower        | Unknown              | Eiffel Tower        |               295 |                 15 |                5 |          0.333 | False        | True                |                3.3202 |
| Resized            | Eiffel Tower        | Unknown              | Eiffel Tower        |               206 |                 11 |                4 |          0.364 | False        | True                |                2.3188 |
| Reduced brightness | Eiffel Tower        | Unknown              | Eiffel Tower        |                59 |                  5 |                4 |          0.8   | False        | True                |                0.6909 |
| Original           | Eiffel Tower        | Unknown              | Statue of Liberty   |              1505 |                312 |                7 |          0.022 | False        | False               |               17.0404 |
| Rotated 25 degrees | Eiffel Tower        | Unknown              | Statue of Liberty   |              1424 |                277 |                8 |          0.029 | False        | False               |               16.249  |
| Resized            | Eiffel Tower        | Unknown              | Statue of Liberty   |              1163 |                191 |                6 |          0.031 | False        | False               |               13.4444 |
| Reduced brightness | Eiffel Tower        | Unknown              | Statue of Liberty   |              1517 |                330 |                8 |          0.024 | False        | False               |               17.0134 |
| Original           | Great Wall of China | Unknown              | Statue of Liberty   |               350 |                 11 |                4 |          0.364 | False        | False               |                3.9186 |
| Rotated 25 degrees | Great Wall of China | Unknown              | Great Wall of China |               510 |                 14 |                7 |          0.5   | False        | True                |                5.6105 |
| Resized            | Great Wall of China | Unknown              | Statue of Liberty   |               298 |                  9 |                4 |          0.444 | False        | False               |                3.2867 |
| Reduced brightness | Great Wall of China | Unknown              | Great Wall of China |                95 |                  5 |                4 |          0.8   | False        | True                |                1.1576 |
| Original           | Great Wall of China | Great Wall of China  | Great Wall of China |              2158 |                175 |              154 |          0.88  | True         | True                |               23.622  |
| Rotated 25 degrees | Great Wall of China | Great Wall of China  | Great Wall of China |              1925 |                178 |              147 |          0.826 | True         | True                |               20.981  |
| Resized            | Great Wall of China | Great Wall of China  | Great Wall of China |               774 |                162 |              147 |          0.907 | True         | True                |                8.6112 |
| Reduced brightness | Great Wall of China | Great Wall of China  | Great Wall of China |               121 |                 36 |               35 |          0.972 | True         | True                |                1.4562 |
| Original           | Great Wall of China | Great Wall of China  | Great Wall of China |              2500 |                121 |               89 |          0.736 | True         | True                |               27.7096 |
| Rotated 25 degrees | Great Wall of China | Great Wall of China  | Great Wall of China |              2500 |                109 |               73 |          0.67  | True         | True                |               27.5153 |
| Resized            | Great Wall of China | Great Wall of China  | Great Wall of China |              2500 |                134 |              108 |          0.806 | True         | True                |               27.6019 |
| Reduced brightness | Great Wall of China | Great Wall of China  | Great Wall of China |              1944 |                100 |               78 |          0.78  | True         | True                |               21.5815 |
| Original           | Great Wall of China | Unknown              | Statue of Liberty   |              2500 |                 94 |                7 |          0.074 | False        | False               |               27.6662 |
| Rotated 25 degrees | Great Wall of China | Unknown              | Statue of Liberty   |              2501 |                 97 |                1 |          0.01  | False        | False               |               27.571  |
| Resized            | Great Wall of China | Unknown              | Statue of Liberty   |              2500 |                 64 |                4 |          0.062 | False        | False               |               27.3815 |
| Reduced brightness | Great Wall of China | Unknown              | Statue of Liberty   |              2501 |                100 |                8 |          0.08  | False        | False               |               27.5336 |
| Original           | Great Wall of China | Unknown              | Eiffel Tower        |              2500 |                102 |                7 |          0.069 | False        | False               |               27.3563 |
| Rotated 25 degrees | Great Wall of China | Unknown              | Taj Mahal           |              2500 |                 81 |                8 |          0.099 | False        | False               |               27.2935 |
| Resized            | Great Wall of China | Unknown              | Statue of Liberty   |              2500 |                 62 |                6 |          0.097 | False        | False               |               27.3517 |
| Reduced brightness | Great Wall of China | Unknown              | Eiffel Tower        |              2500 |                 94 |                7 |          0.074 | False        | False               |               27.4336 |
| Original           | Statue of Liberty   | Unknown              | Taj Mahal           |               775 |                 53 |                8 |          0.151 | False        | False               |                8.7539 |
| Rotated 25 degrees | Statue of Liberty   | Unknown              | Taj Mahal           |              1009 |                 72 |               10 |          0.139 | False        | False               |               11.1489 |
| Resized            | Statue of Liberty   | Unknown              | Statue of Liberty   |               489 |                 20 |                5 |          0.25  | False        | True                |                5.494  |
| Reduced brightness | Statue of Liberty   | Unknown              | Statue of Liberty   |               183 |                 15 |                0 |          0     | False        | True                |                2.1679 |
| Original           | Statue of Liberty   | Unknown              | Colosseum           |               213 |                 26 |                0 |          0     | False        | False               |                2.401  |
| Rotated 25 degrees | Statue of Liberty   | Unknown              | Colosseum           |               268 |                 38 |                6 |          0.158 | False        | False               |                3.0214 |
| Resized            | Statue of Liberty   | Unknown              | Colosseum           |               295 |                 25 |                0 |          0     | False        | False               |                3.2999 |
| Reduced brightness | Statue of Liberty   | Unknown              | Colosseum           |               151 |                 21 |                0 |          0     | False        | False               |                1.7417 |
| Original           | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               725 |                 69 |               53 |          0.768 | True         | True                |                7.9966 |
| Rotated 25 degrees | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               962 |                 82 |               56 |          0.683 | True         | True                |               10.5441 |
| Resized            | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               503 |                 78 |               62 |          0.795 | True         | True                |                5.643  |
| Reduced brightness | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               258 |                 42 |               36 |          0.857 | True         | True                |                2.8688 |
| Original           | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               321 |                164 |              155 |          0.945 | True         | True                |                3.6444 |
| Rotated 25 degrees | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               333 |                170 |              162 |          0.953 | True         | True                |                3.7181 |
| Resized            | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               279 |                126 |              120 |          0.952 | True         | True                |                3.0599 |
| Reduced brightness | Statue of Liberty   | Statue of Liberty    | Statue of Liberty   |               211 |                114 |              108 |          0.947 | True         | True                |                2.3514 |
| Original           | Statue of Liberty   | Unknown              | Statue of Liberty   |               335 |                 12 |                4 |          0.333 | False        | True                |                3.7524 |
| Rotated 25 degrees | Statue of Liberty   | Unknown              | Statue of Liberty   |               488 |                 18 |                5 |          0.278 | False        | True                |                5.3206 |
| Resized            | Statue of Liberty   | Unknown              | Eiffel Tower        |               356 |                 10 |                6 |          0.6   | False        | False               |                3.9659 |
| Reduced brightness | Statue of Liberty   | Unknown              | Statue of Liberty   |               232 |                 13 |                4 |          0.308 | False        | True                |                2.6103 |
| Original           | Taj Mahal           | Taj Mahal            | Taj Mahal           |              1809 |                125 |               84 |          0.672 | True         | True                |               19.7412 |
| Rotated 25 degrees | Taj Mahal           | Taj Mahal            | Taj Mahal           |              2170 |                150 |               82 |          0.547 | True         | True                |               23.6308 |
| Resized            | Taj Mahal           | Taj Mahal            | Taj Mahal           |              1632 |                108 |               70 |          0.648 | True         | True                |               17.7387 |
| Reduced brightness | Taj Mahal           | Taj Mahal            | Taj Mahal           |               645 |                 87 |               63 |          0.724 | True         | True                |                7.1684 |
| Original           | Taj Mahal           | Unknown              | Statue of Liberty   |              1893 |                149 |                6 |          0.04  | False        | False               |               21.0105 |
| Rotated 25 degrees | Taj Mahal           | Unknown              | Statue of Liberty   |              2500 |                202 |                8 |          0.04  | False        | False               |               27.4479 |
| Resized            | Taj Mahal           | Unknown              | Statue of Liberty   |              1643 |                113 |                4 |          0.035 | False        | False               |               18.106  |
| Reduced brightness | Taj Mahal           | Unknown              | Statue of Liberty   |               638 |                 45 |                0 |          0     | False        | False               |                7.1887 |
| Original           | Taj Mahal           | Taj Mahal            | Taj Mahal           |               253 |                137 |              130 |          0.949 | True         | True                |                2.8077 |
| Rotated 25 degrees | Taj Mahal           | Taj Mahal            | Taj Mahal           |               234 |                130 |              126 |          0.969 | True         | True                |                2.5916 |
| Resized            | Taj Mahal           | Taj Mahal            | Taj Mahal           |               131 |                 63 |               63 |          1     | True         | True                |                1.5512 |
| Reduced brightness | Taj Mahal           | Taj Mahal            | Taj Mahal           |                58 |                 43 |               38 |          0.884 | True         | True                |                0.6744 |
| Original           | Taj Mahal           | Unknown              | Statue of Liberty   |              2500 |                170 |                7 |          0.041 | False        | False               |               29.6357 |
| Rotated 25 degrees | Taj Mahal           | Unknown              | Statue of Liberty   |              2500 |                212 |                6 |          0.028 | False        | False               |               29.6073 |
| Resized            | Taj Mahal           | Taj Mahal            | Taj Mahal           |              2500 |                409 |              349 |          0.853 | True         | True                |               29.3205 |
| Reduced brightness | Taj Mahal           | Unknown              | Statue of Liberty   |              2500 |                175 |                7 |          0.04  | False        | False               |               29.4346 |
| Original           | Taj Mahal           | Taj Mahal            | Taj Mahal           |              2500 |                204 |              102 |          0.5   | True         | True                |               27.3511 |
| Rotated 25 degrees | Taj Mahal           | Taj Mahal            | Taj Mahal           |              2500 |                220 |              125 |          0.568 | True         | True                |               27.3599 |
| Resized            | Taj Mahal           | Taj Mahal            | Taj Mahal           |              2500 |                145 |               75 |          0.517 | True         | True                |               27.2473 |
| Reduced brightness | Taj Mahal           | Taj Mahal            | Taj Mahal           |              1782 |                171 |               80 |          0.468 | True         | True                |               19.5256 |

### 5.2 Performance by Test Condition

| condition          |   samples |   recognition_rate |   candidate_accuracy |   mean_matches |   mean_inliers |   mean_processing_time |
|:-------------------|----------:|-------------------:|---------------------:|---------------:|---------------:|-----------------------:|
| Original           |        25 |                 52 |                   56 |         115.4  |          61.92 |                  13.59 |
| Reduced brightness |        25 |                 48 |                   68 |          92.28 |          47.32 |                   9.74 |
| Resized            |        25 |                 52 |                   60 |         105.6  |          71.08 |                  12.47 |
| Rotated 25 degrees |        25 |                 48 |                   68 |         119.52 |          62.2  |                  14.3  |

## 6. Unknown Landmark Test

The unknown-image test has not been recorded. Run the unknown-image test cell and regenerate this report to include its result.

## 7. Performance Analysis

- Total evaluated test cases: 100
- Recognition rate: 50.00% (percentage accepted by the recognition thresholds)
- Candidate classification accuracy: 63.00% (best candidate compared with the true label, including rejected cases)
- Mean processing time: 12.5236 seconds

## 8. Discussion and Limitations

SIFT can identify distinctive local image features and is designed to be reasonably robust to scale and rotation changes. Matching may become less reliable when the query image has a substantially different viewpoint, low resolution, blur, severe illumination changes, or few distinctive features.

A high descriptor match count alone does not guarantee correct recognition. RANSAC provides a geometric consistency check, but homography-based localization can still fail when images show different sides or viewpoints of a three-dimensional landmark.

Recognition thresholds should be evaluated using held-out landmark images and unrelated unknown images. Results in this report reflect only the experiments actually executed.

## 9. Conclusion

This project implements a SIFT-based landmark recognition pipeline that extracts local features, matches descriptors, filters ambiguous matches, ranks candidate landmarks, and uses RANSAC homography estimation for geometric verification and localization. The recorded experimental results provide a basis for assessing its strengths and limitations.
