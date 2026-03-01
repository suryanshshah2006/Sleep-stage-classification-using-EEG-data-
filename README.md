# Sleep-stage-classification-using-EEG-data-

# Sleep Stage Classification using EEG

This repository contains a deep learning framework for the automated classification of sleep stages based on EEG (Electroencephalogram) data. The project utilizes a multi-scale CNN-BiLSTM architecture to achieve high accuracy across various sleep stages.

## Project Overview
Automated sleep stage classification is critical for diagnosing sleep disorders. This project processes raw EEG data, segments it into epochs, and trains a model to recognize five distinct stages:
**W**: Wake 
**N1**: Non-REM Stage 1 
**N2**: Non-REM Stage 2 
**N3**: Non-REM Stage 3 
**REM**: Rapid Eye Movement 

## Dataset & Preprocessing
The project is designed to handle large-scale EEG data by converting raw files into manageable formats:
**Subjects**: Data from 52 subjects was processed and labeled.
**Total Samples**: Approximately 47,090 valid labeled epochs after verification.
**Preprocessing**: Signals are downsampled, normalized (mean-standard deviation scaling), and stored as compressed `.npy` files to optimize training speed.
**Input Shape**: The model uses an input shape of 24 channels and 3,072 timepoints per epoch.



## Model Architecture
The project implements a "Memory-Safe Tuned" SOTA (State-of-the-Art) architecture:
**Multi-Scale CNN**: Dual 1D-Convolutional branches (kernel sizes 32 and 128) capture both fine and coarse temporal features simultaneously.
**Temporal Modeling**: A Bidirectional LSTM (64 units) captures long-term dependencies in the EEG signal.
**Attention Mechanism**: An Attention layer is integrated to focus on the most relevant features within the LSTM output.
**Optimization**: Built with the Adam optimizer and Categorical Crossentropy loss using label smoothing (0.1).



## Performance
The model demonstrates strong predictive performance on the validation set:

### Key Metrics
| Metric | Result |
| :--- | :--- |
| **Final Train Accuracy** | **91.81%** |
| **Final Validation Accuracy** | **83.42%** |

### Classification Report (Validation)
| Stage | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **W (Wake)** | 0.81 | 0.84 | 0.83 |
| **N1** | 0.68 | 0.53 | 0.60 |
| **N2** | 0.86 | 0.89 | 0.87 |
| **N3** | 0.82 | 0.83 | 0.82 |
| **REM** | 0.89 | 0.91 | 0.90 |


