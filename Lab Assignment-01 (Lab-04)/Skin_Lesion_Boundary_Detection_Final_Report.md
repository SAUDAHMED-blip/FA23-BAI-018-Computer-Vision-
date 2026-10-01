# Computer Vision Lab Report

## Skin Lesion Boundary Detection Using Canny Edge Detection

## Objective

The objective of this laboratory experiment is to detect the approximate boundary of a skin lesion using grayscale conversion, Gaussian filtering, Canny edge detection, morphological operations, and contour detection.

## Dataset

HAM10000 Skin Cancer MNIST dataset was downloaded directly using KaggleHub.

## Dataset Information

- Total images discovered: 20030
- Images used in this experiment: 5

## Task 1 — Load the Image

Five skin-lesion images were selected automatically from the downloaded HAM10000 dataset.

- Image 1: `ISIC_0024306`
- Image 2: `ISIC_0026809`
- Image 3: `ISIC_0029313`
- Image 4: `ISIC_0031816`
- Image 5: `ISIC_0034320`

## Task 2 — Preprocessing

Each image was converted from BGR/RGB representation to grayscale. A 5×5 Gaussian filter was then applied to reduce high-frequency noise before edge detection.

## Task 3 — Canny Edge Detection

Three threshold settings were tested:

- 50–100
- 100–200
- 150–250

## Task 4 — Best Canny Result

- `ISIC_0024306` → 50–100
- `ISIC_0026809` → 50–100
- `ISIC_0029313` → 50–100
- `ISIC_0031816` → 50–100
- `ISIC_0034320` → 50–100

## Task 5 — Lesion Boundary Detection

The selected Canny edge map was processed using morphological closing and contour analysis. Candidate contours were evaluated using lesion area and centrality. The selected contour was filled to obtain an approximate lesion mask and then drawn on the original image.

## Task 6 — Lesion Area and Perimeter

| Image | Best Filter | Edge Method | Area (pixels) | Perimeter (pixels) |
|---|---|---|---:|---:|
| Image 1 | Gaussian | Canny | 2487.0 | 798.0 |
| Image 2 | Gaussian | Canny | 60727.5 | 4899.46 |
| Image 3 | Gaussian | Canny | 7068.0 | 400.76 |
| Image 4 | Gaussian | Canny | 96622.5 | 4401.77 |
| Image 5 | Gaussian | Canny | 23420.5 | 3038.03 |

## Final Comparison

| Method | Noise Handling | Edge Density | Contours | Boundary Detection | Overall Performance |
|---|---|---:|---:|---|---|
| Original + Sobel | None | 0.0411 | 89 | Moderate | Moderate |
| Original + Canny | None | 0.005 | 3 | Weak | Weak |
| Average + Sobel | Average filtering | 0.0626 | 111 | Good | Good |
| Average + Canny | Average filtering | 0.0 | 0 | Weak | Weak |
| Gaussian + Sobel | Gaussian filtering | 0.0462 | 110 | Good | Good |
| Gaussian + Canny | Gaussian filtering | 0.0014 | 2 | Weak | Weak |
| Median + Sobel | Median filtering | 0.016 | 24 | Moderate | Moderate |
| Median + Canny | Median filtering | 0.0034 | 4 | Weak | Weak |

## Questions and Answers

### Question 1
Gaussian filtering is applied before Canny edge detection
because real skin images contain noise, hair, small texture
variations, and illumination changes. Gaussian smoothing
reduces high-frequency noise and helps Canny detect stronger
and more meaningful boundaries.

### Question 2
The three threshold settings produced different amounts of
edge information. Lower thresholds such as 50-100 detect more
weak edges but may also detect unwanted texture and noise.
Higher thresholds such as 150-250 suppress weak edges and
usually produce fewer but stronger edges. In this experiment,
the program evaluated 50-100, 100-200, and 150-250 and selected
the threshold giving the strongest central and least noisy
boundary according to the implemented quality measure.

### Question 3
The automatically selected thresholds were evaluated separately
for the five images. The most frequently selected threshold in
this experiment was 50-100. The selection was
based on central edge information and a penalty for excessive
border noise rather than simply choosing the image with the
largest number of edges.

### Question 4
Edges are useful for skin-lesion detection because a lesion
usually has intensity, color, or texture differences from the
surrounding skin. These differences create transitions that
can be represented as edges. Canny detection can therefore
help identify the approximate lesion boundary.

### Question 5
Several problems can occur during lesion-boundary detection.
These include low contrast between the lesion and surrounding
skin, hairs crossing the lesion, illumination variations,
irregular lesion shapes, shadows, and broken Canny edges.
Very low or very high Canny thresholds can also produce either
too many irrelevant edges or too few useful edges.

### Question 6
The method can be improved by using adaptive Canny thresholds,
better color-space analysis such as LAB or HSV, hair removal,
contrast enhancement, morphological operations, contour
filtering, and more advanced segmentation methods. For a true
segmentation accuracy measurement, pixel-level ground-truth
lesion masks would also be required.

## Limitations

The HAM10000 dataset used here does not provide pixel-level segmentation masks for these images. Therefore, a true segmentation accuracy, Dice score, or IoU cannot be calculated from this dataset alone. The reported area and perimeter represent the approximate boundary obtained by the implemented image-processing pipeline.

## Conclusion

The experiment demonstrates a complete skin-lesion boundary-detection pipeline consisting of grayscale conversion, Gaussian filtering, Canny edge detection, morphological processing, contour selection, and lesion area/perimeter calculation. The comparison demonstrates that preprocessing has a significant effect on the quality of detected edges.