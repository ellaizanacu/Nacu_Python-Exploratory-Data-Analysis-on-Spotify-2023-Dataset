# **PYTHON - EXPLORATORY DATA ANALYSIS ON SPOTIFY 2023 DATASET**

This repository contains the python code for performing an exploratory data analysis (EDA) on a dataset of Spotify tracks from 2023. It provides an analysis of a music dataset with a focus on descriptive statistics, top performers, temporal trends, and correlations between musical attributes and popularity metrics. The dataset is analyzed through various exploratory data analysis techniques to gain insights into trends in streaming performance, artist popularity, and platform engagement.

---

## OBJECTIVE:
In this deliverable, the main task is to perform an exploratory data analysis (EDA) on a dataset containing information about popular tracks on Most Streamed Spotify Songs 2023 (https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023Links to an external site.). This task aims to analyze, visualize, and interpret the data to extract meaningful insights.

---

## GENERAL GUIDELINES:
1. Begin by familiarizing yourself with the structure of the dataset. Check for missing values and data types, and perform an initial exploration to understand the different features available.
2. Provide summary statistics to give an overview of key metrics such as the number of streams, release dates, and musical attributes (e.g., BPM, danceability).
3. Use appropriate visualizations (e.g., bar charts, histograms, scatter plots) to uncover trends and patterns in the data. Ensure that your plots are well-labeled and easy to interpret.
4. Investigate correlations between different variables and provide insights based on your findings. Explore relationships between streams and other musical characteristics like tempo, energy, or playlists.
5. Based on your analysis, offer any insights or recommendations regarding the tracks, artists, or musical trends that could be useful for understanding what makes a track popular.

---
## GUIDE QUESTIONS:
The primary goal of this analysis is to explore the dataset, clean any discrepancies, and provide insights based on statistical and visual techniques. The analysis includes answers to the following questions:

### Table of Contents
- [Overview of Dataset](#overview-of-dataset)
- [Basic Descriptive Statistics](#basic-descriptive-statistics)
- [Top Performers](#top-performers)
- [Temporal Trends](#temporal-trends)
- [Genre and Music Characteristics](#genre-and-music-characteristics)
- [Platform Popularity](#platform-popularity)
- [Advanced Analysis](#advanced-analysis)

---

## Overview of Dataset
1. **Rows and Columns**: The dataset contains `X` rows and `Y` columns.
2. **Data Types**: Each column's data type is checked and verified. This includes integers, floats, and categorical types where applicable.
3. **Missing Values**: A review of missing values is conducted to ensure data quality.

### Problem(s):
- **Part A**: How many rows and columns does the dataset contain?
- **Part B**: What are the data types of each column?
- **Part C**: Are there any missing values?

### Approach: 
- Load the dataset, inspect its shape and data types, check for missing values, and replace any non-numeric entries in the `streams` column.

### Functions to be Used:
- `import numpy as np` – imports the NumPy library and aliases it as `np`, useful for handling numerical data and NaN values.
- `import pandas as pd` – imports the Pandas library, aliased as `pd`, for data manipulation and analysis.
- `import matplotlib.pyplot as plt` – imports Matplotlib’s plotting interface, aliased as `plt`, used for visualizations.
- `import seaborn as sns` – imports the Seaborn library for advanced statistical data visualization, built on top of Matplotlib.
- `pd.read_excel()` – reads an Excel file into a Pandas DataFrame.
- `.loc[]` – accesses specific rows and columns by label to modify or view data.
- `print()` – outputs text or variable values to the console.
- `.shape` – returns a tuple indicating the number of rows and columns in the DataFrame.
- `.dtypes` – shows the data type of each column.
- `.isnull().sum()` – counts the number of missing values in each column.

### Code Breakdown:

##### *Overview of Dataset*
```python
# Load the needed libraries for the Exploratory Dataset Analysis
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
# Load the dataset by using the function "pd.read_excel"
Spotify_Data = pd.read_excel('spotify-2023.xlsx')

# Display the first and last few rows to understand the structure of the dataset
Spotify_Data
```

##### *Modified Data*
```python
# Replace non-numeric 'streams' value for "Love Grows (Where My Rosemary Goes)" with NaN
Spotify_Data.loc[Spotify_Data['track_name'] == 'Love Grows (Where My Rosemary Goes)', 'streams'] = np.nan

# Display the modified data to check if the 'streams' value has been set to NaN for the specified track
print("\nModified Data for 'Love Grows (Where My Rosemary Goes)':\n")
Spotify_Data[Spotify_Data['track_name'] == 'Love Grows (Where My Rosemary Goes)']
```

##### *Part A:*
```python
# Display the shape of the dataset (number of rows and columns)
print("Shape of the dataset:", Spotify_Data.shape)
```

##### *Part B:*
```python
# Display the data types of each column
print("\nData types:") 
print(Spotify_Data.dtypes)
```

##### *Part C:*
```python
# Checking for missing values after replacing specific entries with NaN in the 'streams' column only
print("\nMissing values:")
print(Spotify_Data.isnull().sum())
```

### Expected Output: 
- The shape of the dataset, data types for each column, count of missing values, and confirmation that the specified `streams` value is set to NaN.

##### **Overview of Dataset**

![image](https://github.com/user-attachments/assets/655e3939-9391-46a3-a2d3-952aac2e947d)

##### **Modified Data**

![image](https://github.com/user-attachments/assets/2c78e27a-a85c-4dc8-bebd-6fbc96af41e4)

##### *Part A:*

```python
Shape of the dataset: (10000, 15)
```

##### *Part B:*

```python
Data types:
track_name             object
artist_name            object
streams                float64
released_year          int64
artist_count           int64
bpm                    float64
danceability_%         float64
energy_%               float64
valence_%              float64
acousticness_%         float64
key                    int64
mode                   object
spotify_playlists      int64
spotify_charts         int64
apple_playlists        int64
dtype: object
```

##### *Part C:*

```python
Missing values:
track_name             0
artist_name            0
streams                5
released_year          0
artist_count           0
bpm                    2
danceability_%         1
energy_%               0
valence_%              0
acousticness_%         0
key                    0
mode                   0
spotify_playlists      0
spotify_charts         0
apple_playlists        0
dtype: int64
```

--- 

## Basic Descriptive Statistics
1. **Streams Analysis**: 
   - Mean, median, and standard deviation for the `streams` column are calculated to understand central tendencies and dispersion in streaming counts.
2. **Released Year and Artist Count Distribution**: 
   - Analysis of the distribution of the `released_year` and `artist_count` columns.
   - Trends and outliers in release years and artist collaborations are identified.

### Problem(s):
- **Part A**: What are the mean, median, and standard deviation of the streams column?
- **Part B**: What is the distribution of released_year and artist_count? Are there any noticeable trends or outliers?

### Approach:

##### *Part A:*
Use summary statistics methods to get an overview of numerical columns and calculate specific metrics for `streams`.
- `{mean_streams}` – This represents the average number of streams across all tracks.
- `{median_streams}` – The median provides the midpoint of the streams data, less affected by outliers than the mean.
- `{std_streams}` – This measures the spread of stream counts, showing variability in track popularity.

##### *Part B:*
- Use histograms with kernel density estimates (KDE) to visualize the distribution of the release year and artist count.

### Functions to be Used:
- `print()` – outputs text or variable values to the console.
- `.describe()` – generates summary statistics for numerical columns, including count, mean, standard deviation, minimum, quartiles, and maximum.
- `.transpose()` – transposes the DataFrame, swapping rows and columns for easier readability.
- `f-string` – formats strings with embedded variables or expressions, used here to print a line separator.
- `.mean()` – calculates the average (mean) of a specified column.
- `.median()` – calculates the median (middle value) of a specified column.
- `.std()` – calculates the standard deviation of a specified column, showing data dispersion.
- `plt.figure()` – initializes a new figure with a specified size for plotting.
- `sns.histplot()` – creates a histogram plot with optional KDE for visualizing the distribution of data in a specific column.
- `.title()` – adds a title to the plot.
- `.xlabel()` – labels the x-axis.
- `.ylabel()` – labels the y-axis.
- `plt.show()` – displays the plot.

### Code Breakdown:

##### *Part A:*
```python
# Prints introductory text for summary statistics of numerical columns.
print("Summary Statistics for Numerical Columns:\n")

# Generates summary statistics for all numerical columns in Spotify_Data and transposes them for readability.
print(Spotify_Data.describe().transpose())

# Prints a line of dashes (30 characters) as a visual separator.
print(f"{'-'*30}")

# Calculates the mean of the streams column.
mean_streams = Spotify_Data['streams'].mean()

# Calculates the median of the streams column.
median_streams = Spotify_Data['streams'].median()

# Calculates the standard deviation of the streams column.
std_streams = Spotify_Data['streams'].std()

# Prints introductory text for the detailed statistics of the 'streams' column.
print("\nDetailed Statistics for 'Streams' Column:")

# Displays the mean of the streams column.
print("Mean streams:", mean_streams)

# Displays the median of the streams column.
print("Median streams:", median_streams)

# Displays the standard deviation of the streams column.
print("Standard deviation of streams:", std_streams)
```

##### *Part B:*
##### **Distribution of Released Year**
```python
# Initializes a figure with size 10x6 inches for the released_year distribution plot.
plt.figure(figsize=(10, 6))

# Creates a histogram for the 'released_year' column with 20 bins and a KDE overlay.
sns.histplot(Spotify_Data['released_year'], bins=20, kde=True)

# Sets the title of the plot to "Distribution of Released Year".
plt.title('Distribution of Released Year')

# Labels the x-axis as "Released Year".
plt.xlabel('Released Year')

# Labels the y-axis as "Count".
plt.ylabel('Count')

# Displays the plot for the distribution of released_year.
plt.show()
```

##### **Distribution of Artist Count**
```python
# Initializes a new figure with size 10x6 inches for the artist_count distribution plot.
plt.figure(figsize=(10, 6))

# Creates a histogram for the 'artist_count' column with 20 bins and a KDE overlay.
sns.histplot(Spotify_Data['artist_count'], bins=20, kde=True)

# Sets the title of the plot to "Distribution of Artist Count".
plt.title('Distribution of Artist Count')

# Labels the x-axis as "Artist Count".
plt.xlabel('Artist Count')

# Labels the y-axis as "Count".
plt.ylabel('Count')

# Displays the plot for the distribution of artist_count.
plt.show()
```

### Expected Output:
- Summary statistics for all numerical columns, and the mean, median, and standard deviation for the `streams` column.

##### *Part A:*

![image](https://github.com/user-attachments/assets/2b139f95-7500-460a-9e09-275c1ae79a75)
![image](https://github.com/user-attachments/assets/d833ae44-701b-4eb9-96b8-00276e186ef0)

##### *Part B:*

##### **Distribution of Released Year**

![image](https://github.com/user-attachments/assets/1a8e0951-2afa-4bab-86c5-a820208d006b)

##### **Distribution of Artist Count**

![image](https://github.com/user-attachments/assets/9b9d685e-e8ab-4b48-877a-103390d0e1e4)


###### *Note: Only the `streams` column for "Love Grows (Where My Rosemary Goes)" is treated as `NaN`, ensuring other columns retain their original values.*

---

## Top Performers

1. **Top Streamed Tracks**:
   - The track with the highest number of streams is identified.
   - A list of the top 5 most-streamed tracks is provided for further analysis.
2. **Most Frequent Artists**:
   - The top 5 most frequent artists, based on the number of tracks in the dataset, are displayed.

### Problem(s):
- **Part A**: Which track has the highest number of streams? Display the top 5 most streamed tracks.
- **Part B**: Who are the top 5 most frequent artists based on the number of tracks in the dataset?

### Approach:

### Functions to be Used:


### Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

### Expected Output:
- Two histograms showing the distribution of the `released_year` and `artist_count`, helping to identify trends and potential outliers.


---

## Temporal Trends

1. **Tracks Released Over Time**:
   - Analysis of the number of tracks released per year. A line plot is created to show trends in annual releases.
2. **Monthly Release Patterns**:
   - Examination of release patterns by month to identify any seasonal trends.
   - Identification of the month with the highest number of track releases.

### Problem(s):
- **Part A**: Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year.
- **Part B**: Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?

### Approach:

### Functions to be Used:

**Function Used:**
**Description:**

### Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

### Expected Output:

---

## Genre and Music Characteristics

1. **Correlation Analysis**:
   - Examining the relationship between `streams` and attributes like `bpm`, `danceability_%`, and `energy_%`.
   - Insights into which attributes most influence track popularity.
2. **Danceability and Energy Relationship**:
   - Correlation between `danceability_%` and `energy_%` as well as between `valence_%` and `acousticness_%`.

### Problem(s):
- **Part A**: Examine the correlation between streams and musical attributes like bpm, danceability_%, and energy_%. Which attributes seem to influence streams the most?
- **Part B**: Is there a correlation between danceability_% and energy_%? How about valence_% and acousticness_%?

### Approach:

### Functions to be Used:

**Function Used:**
**Description:**

### Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

### Expected Output:

---

## Platform Popularity

1. **Platform Comparison**:
   - Comparison of track counts across platforms (`spotify_playlists`, `spotify_charts`, and `apple_playlists`).
   - Determination of which platform tends to favor popular tracks.

### Problem(s):
- How do the numbers of tracks in spotify_playlists, spotify_charts, and apple_playlists compare? Which platform seems to favor the most popular tracks?

### Approach:

### Functions to be Used:

**Function Used:**
**Description:**

### Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

### Expected Output:

---

## Advanced Analysis

1. **Key and Mode Patterns**:
   - Analysis of streaming patterns among tracks with similar `key` or `mode` (Major vs. Minor).
2. **Genres and Artists in Playlists/Charts**:
   - Identification of genres or artists that appear most frequently in playlists or charts.
   - Comparison of frequently appearing artists across platforms to determine platform-specific preferences.

### Problem(s):
- **Part A**: Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?
- **Part B**: Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.

### Approach:

### Functions to be Used:

**Function Used:**
**Description:**

### Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

### Expected Output:

---

This analysis provides comprehensive insights into the trends and characteristics of popular music tracks, helping to understand what factors contribute to higher stream counts, and how musical attributes and platforms play a role in shaping listener preferences.

### **Overall Conclusion**:
This experiment effectively demonstrates how to filter, transform, and visualize data using Python’s powerful pandas and seaborn libraries. Each problem showcases the ability to manipulate datasets to derive meaningful insights through data wrangling and visualization techniques.

---

###### Author: **Francesca Ellaiza R. Nacu**
