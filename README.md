# Rock-Paper-Scissors Classification using CNNs

**Author:** Arman Rashidizadeh  
**Date:** October 2025  
**Project:** Statistical Methods of Machine Learning

## Project Overview

This project focuses on building and evaluating multiple Convolutional Neural Network (CNN) architectures for classifying hand gesture images representing **Rock**, **Paper**, and **Scissors**.  
Four CNN models (A–D) were developed with **incremental architectural complexity** and **progressive performance improvements**. Model D integrates advanced regularization and residual strategies inspired by lightweight architectures like SqueezeNet, while Model B demonstrated the best overall performance and efficiency.

## Dataset Overview

**Dataset:** Rock-Paper-Scissor-Dataset (Kaggle)  
**Seed:** 42

| Class    | Train    | Val     | Test    | Total    |
| -------- | -------- | ------- | ------- | -------- |
| Paper    | 496      | 106     | 108     | 712      |
| Rock     | 508      | 108     | 110     | 726      |
| Scissors | 525      | 112     | 113     | 750      |
| **All**  | **1531** | **326** | **331** | **2188** |

## Key Details

- **Classes:** Rock, Paper, Scissors
- **Image Format:** PNG, 300x200 px, average size ~ 75KB
- **Distribution:** Balanced (<5% spread) → No class weighting required
- **Corrupt/Missing:** None observed

## Preprocessing Summary

| Step              | Description                                               |
| ----------------- | --------------------------------------------------------- |
| **Resize Target** | 128×128                                                   |
| **Normalization** | Rescale to [0, 1] (divide by 255)                         |
| **Color Space**   | RGB                                                       |
| **Augmentation**  | Random flip, rotation (±8%), zoom (±10%), contrast (±10%) |
| **Split Policy**  | Fixed seed 42 for reproducibility                         |

The dataset was preprocessed and saved as CSV files (train.csv, val.csv, test.csv), each containing image paths and corresponding class labels.

## Project Structure

RockPaperScissors-CNN  
│  
├── Preproc.ipynb # Dataset preprocessing and splitting  
├── Model_A.ipynb # Baseline CNN (simple convolutional model)  
├── Model_B.ipynb # Residual CNN with tuned hyperparameters  
├── Model_C.ipynb # DenseNet-inspired CNN with block compression  
├── Model_D.ipynb # SqueezeFire hybrid CNN with residual links  
│  
├── Project_Report.pdf # Final project report
└── README.md # Overview of dataset, setup, and usage

## Installation & Setup

1. Clone the repository:

```
    git clone https://github.com/<your-username>/RockPaperScissors-CNN.git
    cd RockPaperScissors-CNN
```

2. Install dependencies

```
    pip install -r requirements.txt
```

3. (Optional) If using Kaggle API to fetch the dataset:

```
    kaggle datasets download -d drgfreeman/rockpaperscissors
    unzip rockpaperscissors.zip -d dataset/
```

## Running the Project

1. **Preprocess the dataset**
   - Run `Preproc.ipynb` to resize, normalize, and split images.
2. **Train models**
   - Execute Model_A.ipynb through Model_D.ipynb sequentially.
   - Each notebook trains, validates, and tests a CNN model.
   - Models B, C, and D include KerasTuner-based hyperparameter search.
3. **Evaluate performance**
   - Each notebook produces training/validation accuracy-loss curves and confusion matrices.

## Results Summary

| Model       | Test Accuracy | Test Loss | Notes                               |
| ----------- | ------------- | --------- | ----------------------------------- |
| **Model A** | 0.982         | 0.068     | Simple baseline, sometimes overfits |
| **Model B** | **0.994**     | 0.237     | Best performer, balanced efficiency |
| **Model C** | 0.988         | 0.203     | Dense structure, slower training    |
| **Model D** | 0.948         | 0.419     | High capacity, prone to overfitting |

## License

This project is released for academic and educational purposes only.
All dataset rights belong to the original Kaggle authors.
