# USA House Price Prediction Project

## Overview

This project develops and compares machine learning models to predict house prices in the USA, using a dataset of property features. The goal is to build a robust and accurate model that can provide valuable insights for both buyers and sellers in the real estate market.

## Dataset

The dataset used in this project ( `usa_housing_dataset.csv` ) contains information on various house features, including:

*   **Price:** Sale price of the property (target variable).
*   **Bedrooms:** Number of bedrooms.
*   **Bathrooms:** Number of bathrooms.
*   **Sqft Living:** Square footage of the living area.
*   **Sqft Lot:** Square footage of the lot.
*   **Floors:** Number of floors.
*   **Waterfront:** Whether the property has a waterfront view.
*   **View:** Quality of the view.
*   **Condition:** Condition of the property.
*   **Sqft Above:** Square footage above the basement.
*   **Sqft Basement:** Square footage of the basement.
*   **Yr Built:** Year the property was built.
*   **Yr Renovated:** Year the property was last renovated.
*   **City:** City where the property is located.
*   **Statezip:** State and zip code of the property.

## Project Structure

The repository contains the following files:

*   `house_price_model.ipynb`: A Jupyter Notebook containing the code for data preprocessing, model training, hyperparameter tuning, and evaluation.
*   `house_price_model.pkl`: A saved (pickled) version of the best-performing trained model (Random Forest).
*   `README.md`: This file, providing an overview of the project.

## Dependencies

To run the code in this project, you'll need the following Python packages:

*   pandas
*   numpy
*   scikit-learn
*   matplotlib
*   seaborn
*   xgboost

You can install these packages using pip:
