<p align="center">
  <img src="predictions/00095_t1_72.png" alt="UNET Prediction" width="800">
</p>

# Glioma Segmentation with U-Net on BraTS 2021

This repository contains the implementation of an automatic glioma segmentation pipeline using a U-Net architecture trained on the BraTS 2021 dataset.

The project was developed as the final project for the Imaging AI course in the Master of Science in Data Science program at the University of Luxembourg. The coursework consisted of multiple imaging exercises, culminating in a full deep learning–based medical image segmentation pipeline.

## Project Overview

The goal of this project is to segment glioma subregions from brain MRI scans using deep learning. The pipeline focuses on:

- Data exploration and visualization
- Preprocessing and spatial cropping of 3D MRI volumes
- Training and evaluation of a U-Net segmentation model
- Quantitative evaluation using Dice metrics
- Qualitative visualization of predictions

The implementation uses the MONAI framework on top of PyTorch, following best practices for medical image analysis.

## Dataset

This project uses the BraTS 2021 dataset, which contains multi-modal brain MRI scans with expert-annotated tumor segmentations.

Modalities supported:

- T1
- T1ce
- T2
- FLAIR

Segmentation classes:

- Necrotic core
- Peritumoral edema
- Enhancing tumor

The dataset itself is not included in this repository and must be obtained separately from the official BraTS sources.

## Repository Structure

data/

- BraTS2021_Training_Data
- BraTS2021_Training_Data_Cropped

plots/

- Visualizations of modalities, segmentations, and predictions

predictions/

- Saved model predictions and visual outputs

scripts/

- data/
  - dataloader.py
  - preprocess.py
  - split.py
  - explore.py
  - data_config.json
  - patients_cropping_idxs.json
- model/
  - train.py
  - test.py
  - helpers.py
- utils/
  - vars.py
  - helpers.py

splits/

- Train, validation, and test patient ID splits

main.py

- Entry point for training and testing pipelines

paper.pdf

- Final project report describing methodology and results

presentation.pdf

- Slides used for the project presentation

## Methodology Summary

### Data Preprocessing

- Cropping of empty regions based on segmentation masks
- Resampling to isotropic 1 mm spacing
- Intensity normalization and standardization
- Data augmentation applied during training only

### Model

- U-Net architecture implemented using MONAI
- Dice loss for optimization
- AdamW optimizer with cosine annealing learning rate scheduler
- Early stopping based on validation performance

### Training and Evaluation

- Train/validation/test split: 75% / 15% / 10%
- Optional K-Fold cross-validation
- Evaluation using Dice score (overall and per-class)
- TensorBoard logging for training and validation metrics

### Testing

- Evaluation on held-out test set
- Optional ensemble inference using K-Fold models
- Visualization of predicted segmentation masks

## Imaging AI Coursework Context

This repository corresponds to Task IV of the Imaging AI course, which focuses on deep learning–based medical image segmentation.

Earlier course exercises included:

- Sampling and Fourier analysis of images
- Image enhancement using gamma correction
- Classical threshold-based segmentation methods

These foundational exercises informed the design and interpretation of the final deep learning pipeline.

## How to Run

High-level workflow:

1. Prepare BraTS 2021 data and update paths in scripts/utils/vars.py
2. Run preprocessing and data exploration if needed
3. Train the model using main.py
4. Evaluate the trained model on the test set
5. Visualize predictions and metrics

Exact commands and configurations are documented within the code and paper.

## Disclaimer

This repository is intended for educational and research purposes only.

If you are currently enrolled in a similar course, do not submit this work as your own. Use it strictly as a reference for learning.

## Authors

Anton Zaitsev  
Emmanouil F. Papadimitriou  
Marie Lontsie

Master of Science in Data Science  
University of Luxembourg
