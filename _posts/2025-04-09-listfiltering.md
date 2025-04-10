---
layout: post
title: List & Filtering Homework
toc: False
comments: True
---

# Lists, Searching Algorithms, and Data Analysis with Pandas

## PopCorn Hack 1: Find Students with Scores in a Range

This function filters a DataFrame to return only the rows where the 'Score' falls between `min_score` and `max_score`, inclusive.

```python
def find_students_in_range(df, min_score, max_score):
    return df[(df['Score'] >= min_score) & (df['Score'] <= max_score)]

# Example usage:
find_students_in_range(student_data, 80, 90)
```

---

## PopCorn Hack 2: Calculate Letter Grades

This function adds a new column called `'Letter'` to the DataFrame based on each student's score using standard grading brackets.

```python
def add_letter_grades(df):
    def get_letter(score):
        if score >= 90:
            return 'A'
        elif score >= 80:
            return 'B'
        elif score >= 70:
            return 'C'
        elif score >= 60:
            return 'D'
        else:
            return 'F'
    df['Letter'] = df['Score'].apply(get_letter)
    return df

# Example usage:
add_letter_grades(student_data)
```

---

## PopCorn Hack 3: Find the Mode in a Series

This function returns the most common (mode) value in a Pandas Series. If no mode is found, it returns `None`.

```python
def find_mode(series):
    return series.mode().iloc[0] if not series.mode().empty else None

# Example usage:
find_mode(pd.Series([1, 2, 2, 3, 4, 2, 5]))
```

---

## Load Dataset

This code loads a CSV file into a Pandas DataFrame for further analysis.

```python
import pandas as pd

fire_data = pd.read_csv('data_title.csv')
```

---

## Find Min/Max Average Temperature

This identifies the minimum and maximum values in the `'Temperature'` column.

```python
min_avg_temp = fire_data['Temperature'].min()
max_avg_temp = fire_data['Temperature'].max()

print(f"Min Avg Temp: {min_avg_temp}")
print(f"Max Avg Temp: {max_avg_temp}")
```

---

## Difference Between Max and Min Temp per Incident

This calculates the temperature range for each fire incident by subtracting `'Min Temp'` from `'Max Temp'`.

```python
fire_data['Temp_Diff'] = fire_data['Max Temp'] - fire_data['Min Temp']
fire_data[['Incident ID', 'Temp_Diff']].head()
```

---

## Incidents Exceeding Average Temperature

Filters the dataset to show only incidents where the temperature is higher than the average temperature.

```python
avg_temp = fire_data['Temperature'].mean()
hotter_incidents = fire_data[fire_data['Temperature'] > avg_temp]
hotter_incidents.head()
```

---

## Group by Vegetation and Weather - Average Temp and Wind

Groups the data by vegetation type and weather condition, then calculates the average temperature and wind speed for each group.

```python
grouped_stats = fire_data.groupby(['Vegetation Type', 'Weather Condition'])[['Temperature', 'Wind Speed']].mean().reset_index()
grouped_stats.head()
```

---

## Correlation Between Vegetation Type and Fire Intensity

This calculates the correlation between vegetation type and fire intensity. Since correlation needs numerical values, vegetation type is converted into categorical codes.

```python
fire_data['VegCode'] = fire_data['Vegetation Type'].astype('category').cat.codes
correlation = fire_data[['VegCode', 'Fire Intensity']].corr().iloc[0,1]
print(f"Correlation: {correlation}")
```

Visualize the fire intensity across different vegetation types using a boxplot.

```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))
sns.boxplot(x='Vegetation Type', y='Fire Intensity', data=fire_data)
plt.title('Fire Intensity by Vegetation Type')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

---

## Weather Condition with Highest Average Fire Intensity

This computes and visualizes the average fire intensity for each weather condition.

```python
intensity_by_weather = fire_data.groupby('Weather Condition')['Fire Intensity'].mean().sort_values(ascending=False)
print(intensity_by_weather)
```

Visualize with a bar chart.

```python
sns.barplot(x=intensity_by_weather.index, y=intensity_by_weather.values)
plt.title('Average Fire Intensity by Weather Condition')
plt.xticks(rotation=45)
plt.ylabel('Avg Intensity')
plt.tight_layout()
plt.show()
```

---

## Percentage of Incidents Above 100°F

Calculates the percentage of fire incidents where the temperature was greater than 100°F.

```python
total_incidents = len(fire_data)
over_100 = fire_data[fire_data['Temperature'] > 100]
percentage = (len(over_100) / total_incidents) * 100
print(f"Percentage of Incidents > 100°F: {percentage:.2f}%")
```

---

## Store Fire Data in SQLite

Creates an in-memory SQLite database and stores the fire data in a table named `fire_incidents`.

```python
import sqlite3

conn = sqlite3.connect(':memory:')
fire_data.to_sql('fire_incidents', conn, index=False)
```

---

## SQL Query: Avg Temp and Wind Speed by Vegetation Type

This SQL query retrieves average temperature and wind speed for each vegetation type.

```python
query = """
SELECT "Vegetation Type", AVG("Temperature") as AvgTemp, AVG("Wind Speed") as AvgWind
FROM fire_incidents
GROUP BY "Vegetation Type"
"""
pd.read_sql_query(query, conn)
```

---

## SQL Query: Incidents with Extreme Conditions

Finds fire incidents with temperatures over 120°F and wind speed over 15 mph.

```python
query = """
SELECT * FROM fire_incidents
WHERE "Temperature" > 120 AND "Wind Speed" > 15
"""
pd.read_sql_query(query, conn)
```

---

## SQL Query: Avg Fire Intensity by Weather Condition

Groups fire incidents by weather condition and calculates the average fire intensity for each group.

```python
query = """
SELECT "Weather Condition", AVG("Fire Intensity") as AvgIntensity
FROM fire_incidents
GROUP BY "Weather Condition"
"""
pd.read_sql_query(query, conn)
```

---

## Pandas vs SQL: Comparison Table

| Feature         | Pandas                          | SQL                            |
|----------------|----------------------------------|--------------------------------|
| Ease of Use     | Pythonic, fluent for data ops   | Structured, ideal for queries  |
| Performance     | Fast in-memory for medium data  | Efficient on large datasets    |
| Readability     | Intuitive chaining               | Easy for structured logic      |
| Flexibility     | Great for complex ops + plotting| Best for aggregation/joins     |

---

## Data Visualizations

### Boxplot: Temperature by Vegetation Type

```python
plt.figure(figsize=(12, 6))
sns.boxplot(x='Vegetation Type', y='Temperature', data=fire_data)
plt.title('Temperature Distribution by Vegetation Type')
plt.ylabel('Temperature (°F)')
plt.xlabel('Vegetation Type')
plt.xticks(rotation=45)
plt.show()
```

### Barplot: Avg Fire Intensity by Weather Condition

```python
weather_effect = fire_data.groupby('Weather Condition')['Fire Intensity'].mean().reset_index()

sns.barplot(x='Weather Condition', y='Fire Intensity', data=weather_effect)
plt.title('Effect of Weather Condition on Fire Intensity')
plt.ylabel('Average Fire Intensity')
plt.xlabel('Weather Condition')
plt.xticks(rotation=45)
plt.show()
```

---
