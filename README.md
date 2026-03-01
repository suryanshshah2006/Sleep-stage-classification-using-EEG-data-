# Sleep-stage-classification-using-EEG-data-

# Sleep Stage Classification using EEG

This repository contains a deep learning framework for the automated classification of sleep stages based on EEG (Electroencephalogram) data. The project utilizes a multi-scale CNN-BiLSTM architecture to achieve high accuracy across various sleep stages.

## Project Overview
Automated sleep stage classification is critical for diagnosing sleep disorders. This project processes raw EEG data, segments it into epochs, and trains a model to recognize five distinct stages:
* [cite_start]**W**: Wake [cite: 59, 114]
* [cite_start]**N1**: Non-REM Stage 1 [cite: 60, 115]
* [cite_start]**N2**: Non-REM Stage 2 [cite: 61, 116]
* [cite_start]**N3**: Non-REM Stage 3 [cite: 61, 117]
* [cite_start]**REM**: Rapid Eye Movement [cite: 62, 118]

## Dataset & Preprocessing
The project is designed to handle large-scale EEG data by converting raw files into manageable formats:
* [cite_start]**Subjects**: Data from 52 subjects was processed and labeled[cite: 103, 165].
* [cite_start]**Total Samples**: Approximately 47,090 valid labeled epochs after verification[cite: 169].
* [cite_start]**Preprocessing**: Signals are downsampled, normalized (mean-standard deviation scaling), and stored as compressed `.npy` files to optimize training speed[cite: 177, 202, 262, 550].
* [cite_start]**Input Shape**: The model uses an input shape of 24 channels and 3,072 timepoints per epoch[cite: 443, 506].



## Model Architecture
The project implements a "Memory-Safe Tuned" SOTA (State-of-the-Art) architecture:
* [cite_start]**Multi-Scale CNN**: Dual 1D-Convolutional branches (kernel sizes 32 and 128) capture both fine and coarse temporal features simultaneously[cite: 564, 565, 566].
* [cite_start]**Temporal Modeling**: A Bidirectional LSTM (64 units) captures long-term dependencies in the EEG signal[cite: 572].
* [cite_start]**Attention Mechanism**: An Attention layer is integrated to focus on the most relevant features within the LSTM output[cite: 572].
* [cite_start]**Optimization**: Built with the Adam optimizer and Categorical Crossentropy loss using label smoothing (0.1)[cite: 579, 580].



## Performance
The model demonstrates strong predictive performance on the validation set:

### Key Metrics
| Metric | Result |
| :--- | :--- |
| **Final Train Accuracy** | [cite_start]**91.81%** [cite: 664] |
| **Final Validation Accuracy** | [cite_start]**83.42%** [cite: 665] |

### Classification Report (Validation)
| Stage | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **W (Wake)** | 0.81 | 0.84 | [cite_start]0.83 [cite: 705, 706, 707] |
| **N1** | 0.68 | 0.53 | [cite_start]0.60 [cite: 710, 711, 712] |
| **N2** | 0.86 | 0.89 | [cite_start]0.87 [cite: 715, 716, 717] |
| **N3** | 0.82 | 0.83 | [cite_start]0.82 [cite: 720, 721, 722] |
| **REM** | 0.89 | 0.91 | [cite_start]0.90 [cite: 725, 726, 727] |


