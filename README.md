# Nacu_Python-Exploratory-Data-Analysis-on-Spotify-2023-Dataset

# Spotify Dataset Analysis

## Function List and Descriptions

This section provides an overview of the functions used in the analysis of the Spotify dataset and their respective descriptions.

### 1. `import`

**Function used:**  
- `import numpy as np`, `import pandas as pd`, `import matplotlib.pyplot as plt`, `import seaborn as sns`

**Description:**  
Imports external libraries necessary for data manipulation, numerical operations, and visualization:
- `numpy`: for numerical operations.
- `pandas`: for data handling and analysis.
- `matplotlib.pyplot`: for generating static plots.
- `seaborn`: for statistical data visualization.

---

### 2. `pd.read_excel()`

**Function used:**  
- `Spotify_Data = pd.read_excel('spotify-2023.xlsx')`

**Description:**  
Reads data from an Excel file and loads it into a Pandas DataFrame. This function is used to load the Spotify dataset into the `Spotify_Data` variable.

---

### 3. `Spotify_Data`

**Function used:**  
- `Spotify_Data`

**Description:**  
Refers to the `Spotify_Data` DataFrame, which contains the loaded dataset. Simply referencing it displays the contents of the dataset.

---

### 4. `.loc[]`

**Function used:**  
- `Spotify_Data.loc[Spotify_Data['track_name'] == 'Love Grows (Where My Rosemary Goes)', 'streams'] = np.nan`

**Description:**  
Used to access specific rows and columns by label. In this case, it modifies the `streams` column for the track "Love Grows (Where My Rosemary Goes)" by setting the value to `NaN`.

---

### 5. `np.nan`

**Function used:**  
- `np.nan`

**Description:**  
Represents a missing value in a dataset. Used to replace non-numeric values in the `streams` column with `NaN` for the track "Love Grows (Where My Rosemary Goes)".

---

### 6. `.dtypes`

**Function used:**  
- `Spotify_Data.dtypes`

**Description:**  
Returns the data types of each column in the `Spotify_Data` DataFrame. This helps in understanding the structure of the data and ensuring the appropriate types for calculations.

---

### 7. `.isnull().sum()`

**Function used:**  
- `Spotify_Data.isnull().sum()`

**Description:**  
Checks for missing values (`NaN`) in the DataFrame. `.isnull()` returns a DataFrame of boolean values (`True` for missing values), and `.sum()` counts the `True` values, giving the number of missing entries for each column.

---

### 8. `.describe()`

**Function used:**  
- `Spotify_Data.describe().transpose()`

**Description:**  
Generates summary statistics (count, mean, std, min, max, etc.) for all numerical columns in the dataset. `.transpose()` is used to flip the summary table for better readability.

---

### 9. `.mean()`, `.median()`, `.std()`

**Function used:**  
- `mean_streams = Spotify_Data['streams'].mean()`
- `median_streams = Spotify_Data['streams'].median()`
- `std_streams = Spotify_Data['streams'].std()`

**Description:**  
- `.mean()`: Calculates the mean (average) value of the `streams` column.
- `.median()`: Calculates the median (middle value) of the `streams` column, less sensitive to outliers.
- `.std()`: Calculates the standard deviation of the `streams` column, which measures the spread or variability of the data.

---

### 10. `plt.figure()`

**Function used:**  
- `plt.figure(figsize=(10, 6))`

**Description:**  
Creates a new figure for plotting with the specified dimensions (in this case, 10x6 inches). This is used to set the size of the plot before rendering.

---

### 11. `sns.histplot()`

**Function used:**  
- `sns.histplot(Spotify_Data['released_year'], bins=20, kde=True)`
- `sns.histplot(Spotify_Data['artist_count'], bins=20, kde=True)`

**Description:**  
Creates a histogram to visualize the distribution of numerical data. The `kde=True` argument adds a Kernel Density Estimate (KDE) line to the plot for a smoother distribution curve.

---

### 12. `plt.title()`, `plt.xlabel()`, `plt.ylabel()`

**Function used:**  
- `plt.title('Distribution of Released Year')`
- `plt.xlabel('Released Year')`
- `plt.ylabel('Count')`

**Description:**  
- `plt.title()`: Sets the title of the plot.
- `plt.xlabel()`: Sets the label for the x-axis.
- `plt.ylabel()`: Sets the label for the y-axis.

These functions are used to label and title the visualizations appropriately.

---

### 13. `plt.show()`

**Function used:**  
- `plt.show()`

**Description:**  
Displays the current figure (plot) in the output. This is necessary for rendering the visualizations when using `matplotlib`.

---

### 14. `.dropna()`

**Function used:**  
- `most_streamed = Spotify_Data[['track_name', 'streams']].dropna()`

**Description:**  
Removes any rows containing `NaN` values. In this case, it removes rows with missing values in the `streams` column before performing the sorting operation.

---

### 15. `.sort_values()`

**Function used:**  
- `most_streamed = Spotify_Data[['track_name', 'streams']].dropna().sort_values(by='streams', ascending=False)`

**Description:**  
Sorts the DataFrame based on a specified column. In this case, the `streams` column is sorted in descending order to get the top streamed tracks.

---

### 16. `.value_counts()`

**Function used:**  
- `frequent_artists = Spotify_Data['artist(s)_name'].value_counts()`

**Description:**  
Counts the occurrences of unique values in a categorical column (like `artist(s)_name`) and returns the frequency of each value in descending order.

---

### 17. `sns.barplot()`

**Function used:**  
- `sns.barplot(x='streams', y='track_name', data=most_streamed, palette='coolwarm')`

**Description:**  
Creates a bar plot to visualize categorical data. In this case, it visualizes the top 5 tracks by `streams`. The `palette` argument specifies the color palette used in the plot.

---

### 18. `plt.bar()`

**Function used:**  
- `plt.bar(frequent_artists.index, frequent_artists.values, color=plt.cm.Pastel1(range(len(frequent_artists))))`

**Description:**  
Generates a bar chart with specified x-values (artist names) and y-values (the count of tracks per artist). The `color` argument is used to apply a custom color palette to the bars.

---

### 19. `plt.xticks()`

**Function used:**  
- `plt.xticks(rotation=45, ha='right')`

**Description:**  
Rotates the x-axis tick labels to make them more readable, especially when there are many categories (like artist names). The `ha='right'` argument aligns the labels to the right.

---

This concludes the list of functions used in the analysis of the Spotify dataset and their descriptions. Each function serves a specific purpose to clean, analyze, and visualize the data effectively.
