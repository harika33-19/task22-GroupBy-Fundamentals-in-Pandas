# task22-GroupBy-Fundamentals-in-Pandas

## Objective
Use Pandas `groupby()` to summarize numerical data across categories and groups. This task demonstrates grouping, aggregation, and basic exploratory data analysis.

## Tools Used
- Python
- Pandas
- Google Colab or Jupyter Notebook

## Dataset
A small student dataset is created directly in Python, so no external CSV file is required.

```python
import pandas as pd

data = {
    "Name": ["Ravi", "Priya", "Arun", "Sneha", "Kiran", "Divya"],
    "Department": ["CSE", "ECE", "CSE", "ECE", "CSE", "ECE"],
    "Gender": ["Male", "Female", "Male", "Female", "Male", "Female"],
    "Marks": [80, 90, 70, 85, 95, 75],
    "Attendance": [85, 90, 80, 95, 88, 92]
}

df = pd.DataFrame(data)
print(df)
```

## Examples

### 1. Sum of marks by department
```python
print(df.groupby("Department")["Marks"].sum())
```
Interpretation: CSE has 245 total marks and ECE has 250 total marks.

### 2. Average marks by department
```python
print(df.groupby("Department")["Marks"].mean())
```
Interpretation: CSE averages about 81.67, while ECE averages about 83.33.

### 3. Count students by department
```python
print(df.groupby("Department")["Name"].count())
```
Interpretation: Both CSE and ECE have three students.

### 4. Minimum marks by department
```python
print(df.groupby("Department")["Marks"].min())
```
Interpretation: The minimum is 70 for CSE and 75 for ECE.

### 5. Maximum marks by department
```python
print(df.groupby("Department")["Marks"].max())
```
Interpretation: The maximum is 95 for CSE and 90 for ECE.

### 6. All summary statistics together
```python
summary = df.groupby("Department")["Marks"].agg(
    ["sum", "mean", "count", "min", "max"]
)
print(summary)
```

### 7. Group by multiple columns
```python
print(df.groupby(["Department", "Gender"])["Marks"].mean())
```
This groups by both department and gender. In this sample data, CSE has male students and ECE has female students, so only two combinations appear.

### 8. Average marks and attendance by department
```python
print(df.groupby("Department")[["Marks", "Attendance"]].mean())
```

## Important Concepts
- `groupby()` divides rows into groups based on one or more columns.
- Aggregation summarizes each group.
- `sum()` calculates a total.
- `mean()` calculates an average.
- `count()` counts non-missing values.
- `min()` returns the smallest value.
- `max()` returns the largest value.
- Use actual column names in `groupby()`. For example, `"column_name"` and `"numeric_column"` are placeholders and will cause a `KeyError` unless those columns actually exist.

## Common Error: KeyError
If you get `KeyError: 'column_name'`, check the real column names:
```python
print(df.columns)
print(df.head())
```
Then replace placeholder names with actual column names, such as:
```python
df.groupby("Department")["Marks"].sum()
```

## Conclusion
Pandas `groupby()` makes it easy to compare categories and summarize numerical data. These techniques are useful for exploratory data analysis and data science projects.
