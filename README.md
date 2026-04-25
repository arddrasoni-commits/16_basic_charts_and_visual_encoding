# 16_basic_charts_and_visual_encoding
# Arddra Soni
# PRN: 25070123022
## Overview

This experiment explores **basic charts and visual encoding** using Python's data visualization libraries. A student performance dataset spanning a week (Monday to Friday) is created and visualized through multiple chart types to understand relationships, trends, distributions, and comparisons across variables like study hours, marks, attendance, sleep hours, and assignments completed.

---

## Libraries Used

### 1. **Pandas**
Used for creating and managing structured tabular data via `DataFrame`. It serves as the backbone for storing the dataset and makes it easy to access individual columns for plotting.

### 2. **NumPy**
Imported for numerical operations. While not heavily used in this experiment directly, it supports data manipulation and is a dependency for other libraries.

### 3. **Matplotlib (`matplotlib.pyplot`)**
The primary plotting library used throughout the experiment. It provides fine-grained control over chart creation, including customization of colors, markers, labels, titles, grids, and annotations. All raw chart creation is done through `plt` functions.

### 4. **Seaborn**
A higher-level visualization library built on top of Matplotlib. It produces aesthetically cleaner charts with less code. Used at the end of the experiment to recreate the line plot and histogram with improved default styling.

---

## Dataset

Two datasets are used:

**Dataset 1 (Student Weekly Performance):**

| Column | Description |
|--------|-------------|
| `days` | Days of the week (Mon–Fri) |
| `hours` | Study hours per day |
| `Marks` | Test marks |
| `Attendance` | Attendance percentage |
| `Sleep_hours` | Hours of sleep |
| `Assignments_completed` | Number of assignments done |

**Dataset 2 (Extended Marks Distribution):**
A list of 19 mark values used for the histogram to demonstrate frequency distribution.

---

## Charts and Their Purpose

### 1. **Basic Line Chart** — Trend Visualization

```python
plt.plot(df['days'], df['hours'], marker='o')
```

Shows how study hours change across the week. The `marker='o'` adds circular data points for clarity. This chart reveals **trends over time**.

---

### 2. **Advanced Line Chart** — Styled Trend

```python
plt.plot(df['days'], df['hours'], marker='*', color='red', label='Marks')
```

Same data as the basic line chart but enhanced with a star marker, red color, and a legend. Demonstrates how visual encoding (color, marker style, labels) improves chart readability.

---

### 3. **Basic Bar Chart** — Comparison

```python
plt.bar(df['days'], df['Marks'], color='skyblue')
```

Displays marks for each day as vertical bars. Bar charts are ideal for **comparing discrete categories**.

---

### 4. **Advanced Bar Chart** — With Data Labels and Grid

```python
for bar in bars:
    y = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2, y, str(y), ha='center', va='bottom')
plt.grid(axis='y')
```

Builds on the basic bar chart by adding:
- **Value labels** on top of each bar using `plt.text()`
- A **horizontal grid** for easier reading

---

### 5. **Histogram** — Distribution Analysis

```python
plt.hist(df['marks'], bins=8, edgecolor='red', alpha=1)
```

Uses the extended marks dataset to show how marks are **distributed across ranges (bins)**. The `bins=8` parameter divides the data into 8 intervals. Red edge color separates bars clearly.

---

### 6. **Basic Scatter Plot** — Relationship Between Variables

```python
plt.scatter(df['hours'], df['Marks'], color='green')
```

Plots study hours (x-axis) against marks (y-axis) to reveal **correlations or relationships**. A positive trend is visible — more study hours generally correspond to higher marks.

---

### 7. **Conditional Scatter Plot** — Category-Based Color Encoding

```python
df['result'] = ['Fail', 'Pass', 'Fail', 'Pass', 'Pass']
colors = ['red' if result == 'Fail' else 'green' for result in df['result']]
plt.scatter(df['hours'], df['Marks'], c=colors)
```

Adds a categorical variable `result` (Pass/Fail) and encodes it using **color** — red for Fail, green for Pass. This is a powerful visual encoding technique to highlight categories within a scatter plot.

---

### 8. **Seaborn Line Plot** — Cleaner Trend Visualization

```python
sns.lineplot(data=df, x='days', y='hours')
```

Recreates the line chart using Seaborn, which automatically applies a polished theme and handles data more intuitively with the `data=` parameter.

---

### 9. **Seaborn Histogram** — Distribution with KDE Support

```python
sns.histplot(data=df, x='Marks')
```

Produces a cleaner histogram compared to the Matplotlib version. Seaborn's `histplot` also supports optional KDE (Kernel Density Estimation) overlays for smooth distribution curves.

---

## Key Concepts Demonstrated

| Concept | Example |
|---------|---------|
| **Trend** | Line charts showing study hour changes |
| **Comparison** | Bar charts comparing marks per day |
| **Distribution** | Histogram of mark frequencies |
| **Relationship** | Scatter plot of hours vs. marks |
| **Visual Encoding** | Color, markers, labels, grids |
| **Categorical Encoding** | Red/green coloring in scatter plot |

---

## Conclusion

This experiment demonstrates that the same data can be communicated in different ways depending on the chart type chosen. Matplotlib gives developers precise control over every visual element, while Seaborn simplifies the process with better default aesthetics. Together, these libraries form a comprehensive toolkit for data visualization in Python, covering trends, comparisons, distributions, and relationships — the four fundamental types of data stories.
