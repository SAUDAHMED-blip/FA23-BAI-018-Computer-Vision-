# FA23-BAI-018 — CNN Feature Visualization, Parameter Audit & Critical Analysis

**Student:** Saud Ahmed  
**Registration:** FA23-BAI-018  
**Lab:** 12 (Assignment)  
**Course:** Computer Vision / Deep Learning

## Run in Google Colab
1. Upload `FA23-BAI-018_CNN_Feature_Visualization.ipynb` to [Google Colab](https://colab.research.google.com/).
2. Select Runtime > Run all. CPU is sufficient. The setup cell installs KaggleHub and torchinfo.
3. The notebook downloads the public [Intel Image Classification dataset](https://www.kaggle.com/datasets/puneet6060/intel-image-classification) directly. If prompted, authenticate using `kagglehub.login()`; never commit credentials.
4. Save the notebook with outputs and download `CNN_Lab12_Evidence.zip` from Colab's Files panel.

## Assignment coverage
- Five explicit kernels: Sobel X, Sobel Y, sharpen, box blur, emboss.
- Four stages: raw convolution, ReLU, max pooling and average pooling.
- 5 × 4 grid with colorbars, feature-map statistics, and activation comparisons.
- Two independent RGB 32 × 32 CNN architectures, framework summaries and parameter audit.
- Five critical analysis questions, including live pixel evidence, receptive fields and a tested commutativity proof.

| Model | Kernel | Pooling | Expected trainable parameters |
|---|---|---|---:|
| A | 3×3 | Max | 710 |
| B | 5×5 | Average | 1750 |

Parameter increase: 146.478873%. Pooling after each convolution is a design choice. Models are untrained: the six-category Kaggle dataset supplies only the visualization image; the audit models have ten outputs as required.

## Submission evidence
The assignment additionally requires handwritten parameter calculations, actual framework summary screenshots, and a viva. Run the notebook to generate genuine results, inspect the marked image regions, and prepare your handwritten work. The source dataset is credited to Intel's scene classification challenge and Puneet Bansal's Kaggle distribution. No dataset files or credentials are included in this repository.

## Repository folder
`LAB 12(ASSIGNMENT)/` contains this README and the notebook. Suggested standalone repository name: `FA23-BAI-018-CNN-Feature-Visualization`.
