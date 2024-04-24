# World Population Data Analysis using Python

## Overview
This repository contains Python code for analyzing world population data using Pandas, Seaborn, and Matplotlib libraries. The code performs various data analysis tasks and generates visualizations to gain insights into global population trends.

## File Structure
- `population_analysis.py`: Python script for data analysis and visualization.
- `world_population.csv`: Input data file containing world population data.

## Setup
1. Clone the repository to your local machine.
2. Ensure you have Python installed along with the required libraries (`pandas`, `seaborn`, `matplotlib`).
3. Open the terminal and navigate to the project directory.
4. Run the Python script using the command `python population_analysis.py`.

## Functionality
```python
#!/usr/bin/env python
# coding: utf-8

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv(r'C:\Users\Rhugved\Desktop\Python for DA\world_population.csv')

# Set decimal formatting
pd.set_option('display.float_format', lambda x: '%.2f' % x)

# Display basic info about the data
print("Data Info:")
print(df.info())

# Descriptive statistics
print("\nDescriptive Statistics:")
print(df.describe())

# Check for missing values
print("\nMissing Values:")
print(df.isnull().sum())

# Number of unique values in each column
print("\nUnique Values:")
print(df.nunique())

# Sort data by population in descending order and display top 10 entries
print("\nTop 10 Entries by Population:")
print(df.sort_values(by="2022 Population", ascending=False).head(10))

# Correlation between numerical columns
print("\nCorrelation Matrix:")
print(df.corr())

# Heatmap using Seaborn
sns.heatmap(df.corr(), annot=True)
plt.rcParams['figure.figsize'] = (40, 7)
plt.show()
```

![image](https://github.com/RhugvedSatardekar/Python-Exploratory-Data-Analysis-using-Pandas-and-Seaborn/assets/163725285/228f0a5e-7750-4f28-9496-c78070253a2c)

```python 
# Group by continent and calculate mean population values over different years
print("\nMean Population by Continent:")
print(df.groupby('Continent').mean().sort_values(by="2022 Population", ascending=False))

# Plotting mean population over years
df2 = df.groupby('Continent')[['2022 Population', '2020 Population', '2015 Population', '2010 Population', '2000 Population', '1990 Population', '1980 Population', '1970 Population']].mean().sort_values(by="2022 Population", ascending=False)
df2.transpose().plot()
```
![image](https://github.com/RhugvedSatardekar/Python-Exploratory-Data-Analysis-using-Pandas-and-Seaborn/assets/163725285/b25a7408-bb8c-4151-b95d-900fde3283d9)

```python
# Boxplot for outliers
df.boxplot(figsize=(20, 10))
plt.show()
```


![image](https://github.com/RhugvedSatardekar/Python-Exploratory-Data-Analysis-using-Pandas-and-Seaborn/assets/163725285/f48d7015-0f95-4f95-ab3e-0f62ba52dc53)

``` python
# Data types of columns
print("\nData Types:")
print(df.dtypes)

# Selecting numeric columns
print("\nNumeric Columns:")
print(df.select_dtypes(include='number'))

# Selecting float columns
print("\nFloat Columns:")
print(df.select_dtypes(include='float'))

# Selecting object columns
print("\nObject Columns:")
print(df.select_dtypes(include='object'))
```
