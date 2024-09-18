# EEG Time Series Anomaly Detection

This project presents an approach, methodology, and results for detecting anomalies in an EEG time series dataset. The objective is to classify subjects into alcoholic and control categories using various anomaly detection algorithms after performing data preparation, feature extraction, and model evaluation.

## Table of Contents
- [Project Overview](#project-overview)
- [Data Preparation](#data-preparation)
- [Data Visualization](#data-visualization)
- [Feature Extraction](#feature-extraction)
- [Anomaly Detection](#anomaly-detection)
- [Challenges](#challenges)
- [Future Work](#future-work)

## Project Overview

The primary goal of this project was to analyze real-world EEG data, perform feature extraction, and evaluate different anomaly detection techniques. The dataset consists of EEG recordings from both alcoholic and control subjects. Anomaly detection was performed using several techniques, with the Local Outlier Factor (LOF) algorithm emerging as the best performer.

## Data Preparation

- **Small Dataset**: Initially, I analyzed a small dataset containing EEG recordings from one alcoholic subject and one control subject. This helped me understand the dataset's attributes and structure.
- **Large Dataset**: I consolidated the data from the `SMNI_CMI_TRAIN` and `SMNI_CMI_TEST` folders into a single dataframe. This dataset included EEG trials for different subjects, classified into alcoholic and control categories. The consolidated dataset was over 730 MB in size and contained no missing values.
- **Columns**: The first four columns (Trial, Sensor, Sample, Sensor_Value) were directly extracted from trial files, and an additional column "Type" was added to label the subject type (0 for control, 1 for alcoholic).

## Data Visualization

I created 3D graphs for visualizing the EEG signals across different subjects and trials. These plots highlighted the differences between alcoholic and control subjects, with higher overall values in the EEG signals of alcoholic subjects.

## Feature Extraction

To extract meaningful information from the EEG time series data, I used:
- **Statistical Features**: Mean, median, variance, skewness, and kurtosis were calculated from the "Sensor_Value" column over a window size of 100 samples.
- **Fast Fourier Transform (FFT)**: I attempted to extract frequency-based features using FFT, but due to computational limitations, the process took too long to generate complete results.

## Anomaly Detection

The dataset was split into an 80:20 train-test ratio, and I tested three anomaly detection algorithms:
- **Isolation Forest**
- **One-class SVM**
- **Local Outlier Factor (LOF)**: LOF emerged as the best performer with an accuracy of 51.2%. It assigns anomaly scores based on the local density deviation of data points.
- **Cluster-Based Local Outlier Factor (CBLOF)**: This method extends LOF by clustering data points before calculating their anomaly scores. I evaluated this method using the AUC-ROC score and visualized the ROC curve.

### Model Performance

The models were evaluated based on F1 score, precision, and recall. Accuracy was not used due to the nature of the anomaly detection task. Hyperparameter tuning did not significantly improve model performance, likely due to limitations in feature extraction.

## Challenges

- **EEG Domain Knowledge**: My limited knowledge of EEG signal processing impacted my ability to extract advanced features from the dataset.
- **Computational Constraints**: The size of the dataset and lack of computational resources affected the speed and scope of feature extraction.
- **Small Dataset**: The dataset used for analysis was relatively small, which may have affected model performance.

## Future Work

To improve my analysis, I plan to:
- Collate the full EEG dataset, which includes more subjects (122 total).
- Explore advanced feature extraction techniques to derive better features.
- Implement autoencoders for anomaly detection.
- Further optimize models with hyperparameter tuning and explore additional anomaly detection algorithms.

## Conclusion

In this project, I applied various anomaly detection techniques to an EEG time series dataset. LOF emerged as the best-performing algorithm, but the overall accuracy of 51.2% reflects the complexity of classifying EEG signals. The groundwork laid in this project offers a foundation for future analysis of EEG data and anomaly detection.

