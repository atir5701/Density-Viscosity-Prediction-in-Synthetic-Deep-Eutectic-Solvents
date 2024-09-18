# Predicting Thermophysical Properties of Deep Eutectic Solvents (DESs) using ANN and XGBoost 

This project explores the use of Artificial Neural Networks (ANN) and the Extreme Gradient Boosting Model (XGBoost) to estimate the density and viscosity of synthesized Deep Eutectic Solvents (DESs). The goal is to predict these thermophysical properties with high accuracy, facilitating broader utilization of DESs in industrial applications.

## Introduction
Deep Eutectic Solvents (DESs) are gaining significant attention due to their potential applications in various industries. Understanding and predicting their thermophysical properties, such as density and viscosity, is critical to expanding their use.
This project focuses on building a reliable tool for predicting the density and viscosity of DESs using machine learning models. The investigation involved developing an Extreme Gradient Boosting Model (XGBoost) to estimate the properties of 40 synthesized DESs.

## Dataset
Density: 494 data points collected within the temperature range of 308 to 353 K.
Viscosity: 1600 data points collected within the temperature range of 293.15 to 323.15 K.
Hydrogen Bond Acceptors and Donors: DESs were synthesized by varying the molar ratio of three hydrogen bond acceptors and three hydrogen bond donors.

## Pre-processing
  - ### Feature Selection:  
    Key features like Temperature, MCI, Acentric Factor, and Molecular Weight were selected based on expert insights to ensure high relevance in predicting both density and viscosity.
  - ### Data Normalization:
    Z-score normalization was applied to scale the dataset to a standardized range (0 to 1), enhancing the robustness and reliability of the models.

## Modeling
- The dataset was used to train two separate XGBoost models:
   One for density prediction.
   One for viscosity prediction.

- ### Handling Density Prediction
    Linear Relationship: The relationship between density and temperature in the dataset was found to be linear. Therefore, the XGBoost model for density prediction was directly trained using the preprocessed dataset.
    Input Features: Temperature, MCI, Acentric Factor, Molar Ratio, and Molecular Weight.
    Output Feature: Density.

- ### Handling Viscosity Prediction
    Non-linear Relationship: The relationship between viscosity and temperature was non-linear. To address this, a preprocessing step was added where the inverse of temperature (1/Temp) was used as a feature instead of the direct temperature.
    Input Features: MCI, Molar Ratio, Acentric Factor, Molecular Weight, and 1/Temp.
    Output Feature: Viscosity.

- ### XGBoost Hyperparameter Tuning
  To improve model performance, the following hyperparameters were fine-tuned:

  Objective Function: The best objective function was found to be Tweedie for both density and viscosity prediction.
  Learning Rate: 0.015
  Max Depth: 6  

## Results
The XGBoost model demonstrated high accuracy in predicting the thermophysical properties of DESs:

- ### Density:
  MAPE: 0.16%
  R² Score: 0.9965

- ### Viscosity:
  MAPE: 1.55%
  R² Score: 0.9961

The linear relationship for density allowed for direct training, while the non-linear relationship for viscosity required an inversion of the temperature feature, leading to better model performance.\

## Dependencies
  1) Python 3.x
  2) Pandas
  3) NumPy
  4) Scikit-learn
  5) XGBoost
