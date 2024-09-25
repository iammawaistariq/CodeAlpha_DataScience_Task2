# CodeAlpha_DataScience_Task2
CodeAlpha 3-Month Data Science Internship - Task 2 (September)

# NASA Meteorite Landings Dataset - Data Preprocessing

This repository contains the complete data preprocessing pipeline for the **NASA Meteorite Landings Dataset**. This dataset tracks meteorites that have landed on Earth, including information about their mass, location, and date of impact. The full dataset has over 43,000 entries and contains missing values, outliers, and a mix of numerical and categorical features.

## Dataset Overview

The **NASA Meteorite Landings Dataset** is sourced from [NASA's Open Data Portal](https://data.nasa.gov/Space-Science/Meteorite-Landings/gh4g-9sfh).

### Key Features:
- `name`: Name of the meteorite
- `id`: Unique identifier for each meteorite
- `nametype`: Valid or Relict type of the meteorite
- `recclass`: Classification of the meteorite
- `mass (g)`: Mass of the meteorite (in grams)
- `fall`: Indicates if the meteorite "Fell" or was "Found"
- `year`: Year when the meteorite was found
- `reclat`: Latitude where the meteorite was found
- `reclong`: Longitude where the meteorite was found

### Data Preprocessing Steps:
This repository provides Python code to handle the following preprocessing tasks:
1. **Handling Missing Values**
2. **Detecting and Handling Outliers**
3. **Normalizing and Scaling Features**
4. **Splitting Data into Training and Testing Sets**

---

## Data Preprocessing Steps

This section details the preprocessing steps applied to the **NASA Meteorite Landings Dataset**. The preprocessing addresses missing values, outliers, feature scaling, and data splitting to ensure the dataset is ready for analysis or machine learning tasks.

### 1. Handling Missing Values
The dataset contains missing values in several columns, such as `mass (g)`, `year`, and `geolocation`. We handled these missing values as follows:
- **Column Removal**: The `geolocation` column was dropped due to excessive missing data.
- **Imputation**: 
  - The `mass (g)` column, which had a wide range of values and outliers, was filled using the median value.
  - The `year` column, treated as a categorical-like feature, was filled using the mode (most frequent year).

### 2. Detecting and Handling Outliers
Outliers, especially in the `mass (g)` column, can distort data interpretation and model performance. To address this:
- **Outlier Detection**: We visualized the distribution of meteorite mass using a boxplot, which highlighted significant outliers.
- **IQR Method**: We applied the Interquartile Range (IQR) method to identify and remove extreme outliers. Any values falling outside 1.5 times the IQR from the first or third quartiles were considered outliers and excluded.

### 3. Normalizing and Scaling Features
Numerical features in the dataset, such as `mass (g)`, `reclat` (latitude), and `reclong` (longitude), vary widely in scale. To standardize these features:
- **Min-Max Scaling**: We applied Min-Max Scaling to normalize the numerical columns to a [0,1] range. This ensures that features like `mass (g)` are on a comparable scale to others.
- **Latitude and Longitude**: The geographic coordinates (`reclat` and `reclong`) were scaled to ensure uniformity across all numerical features.

### 4. Splitting Data into Training and Testing Sets
To prepare the dataset for machine learning, we split it into training and testing sets:
- **Feature Selection**: The normalized features, including `mass_scaled`, `reclat`, and `reclong`, were selected as input features.
- **Training/Testing Split**: The dataset was divided into training and testing sets, with 70% of the data used for training and 30% reserved for testing. This ensures that the model is evaluated on unseen data for reliable performance assessment.
