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

## Preprocessing Steps

### 1. Handling Missing Values
Several columns in the dataset contain missing values, which we handle as follows:
- **Dropping Columns**: Columns with too many missing values (e.g., `geolocation`) are dropped.
- **Imputation**: Missing values in the `mass (g)` column are filled with the median value, while the `year` column is filled with the mode (most common year).

```python
# Fill missing values
df['mass (g)'] = df['mass (g)'].fillna(df['mass (g)'].median())
df['year'] = df['year'].fillna(df['year'].mode()[0])

