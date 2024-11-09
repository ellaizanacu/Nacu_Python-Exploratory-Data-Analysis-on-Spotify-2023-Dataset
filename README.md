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

## Problem(s):
- **Part A**: How many rows and columns does the dataset contain?
- **Part B**: What are the data types of each column?
- **Part C**: Are there any missing values?

## Approach: 
- Load the dataset, inspect its shape and data types, check for missing values, and replace any non-numeric entries in the `streams` column.

## Functions to be Used:

##### *Overview of Dataset*
  - **`Function:`** `import numpy as np`
    - **`Description:`** Imports the NumPy library and assigns it the alias `np`, which is commonly used for numerical operations in Python.

  - **`Function:`** `import pandas as pd`
    - **`Description:`** Imports the Pandas library and assigns it the alias `pd`, which is used for data manipulation and analysis.

  - **`Function:`** `import matplotlib.pyplot as plt`
    - **`Description:`** Imports the `pyplot` module from Matplotlib and assigns it the alias `plt`, commonly used for creating visualizations.

  - **`Function:`** `import seaborn as sns`
    - **`Description:`** Imports the Seaborn library, a statistical data visualization library based on Matplotlib, and assigns it the alias `sns`.

  - **`Function:`** `Spotify_Data = pd.read_excel('spotify-2023.xlsx')`
    - **`Description:`** Reads the Excel file `'spotify-2023.xlsx'` into a Pandas DataFrame named `Spotify_Data`. This file is assumed to contain the Spotify dataset.

  - **`Function:`** `Spotify_Data`
    - **`Description:`** Displays the first and last few rows of the DataFrame `Spotify_Data`, allowing a quick overview of the dataset's structure and contents.

##### *Modified Data*
  - **`Function:`** `Spotify_Data.loc[Spotify_Data['track_name'] == 'Love Grows (Where My Rosemary Goes)', 'streams'] = np.nan`
    - **`Description:`** Locates the row in `Spotify_Data` where the 'track_name' is 'Love Grows (Where My Rosemary Goes)' and replaces the 'streams' value with `np.nan` (representing a missing value). This helps clean the data by setting non-numeric values in 'streams' to `NaN`.

  - **`Function:`** `print("\nModified Data for 'Love Grows (Where My Rosemary Goes)':\n")`
    - **`Description:`** Prints a label to indicate the output, specifically showing the modified data for the specified track, followed by newline characters for better readability.

  - **`Function:`** `Spotify_Data[Spotify_Data['track_name'] == 'Love Grows (Where My Rosemary Goes)']`
    - **`Description:`** Filters `Spotify_Data` to display only the row where 'track_name' is 'Love Grows (Where My Rosemary Goes)', allowing verification that the 'streams' value was correctly modified.

##### *Part A:*
  - **`Function:`** `Spotify_Data.shape`
    - **`Description:`** Returns the shape of the `Spotify_Data` DataFrame, which represents the number of rows and columns in the dataset.

  - **`Function:`** `print("Shape of the dataset:", Spotify_Data.shape)`
    - **`Description:`** Prints the shape of the `Spotify_Data` dataset, giving an overview of its dimensions (number of rows and columns).
      
##### *Part B:*
  - **`Function:`** `Spotify_Data.dtypes`
    - **`Description:`** Returns the data types of each column in the `Spotify_Data` DataFrame, helping to understand the type of data (e.g., integer, float, object) in each column.

  - **`Function:`** `print("\nData types:")`
    - **`Description:`** Prints a label "Data types" followed by a newline, providing context for the output of the data types.

  - **`Function:`** `print(Spotify_Data.dtypes)`
    - **`Description:`** Prints the data types of each column in the `Spotify_Data` DataFrame, allowing the user to verify the data type of every column in the dataset.

##### *Part C:*
  - **`Function:`** `Spotify_Data.isnull()`
    - **`Description:`** Checks each entry in the `Spotify_Data` DataFrame to determine if it contains a missing value (i.e., `NaN`).

  - **`Function:`** `Spotify_Data.isnull().sum()`
    - **`Description:`** Sums the boolean values returned by `isnull()`, counting the total number of missing values (`NaN`) in each column of the `Spotify_Data` DataFrame.

  - **`Function:`** `print("\nMissing values:")`
    - **`Description:`** Prints a label "Missing values:" followed by a newline to provide context for the output of missing value counts.

  - **`Function:`** `print(Spotify_Data.isnull().sum())`
    - **`Description:`** Prints the total count of missing values for each column in the `Spotify_Data` DataFrame, helping to identify if there are any `NaN` values remaining after data cleaning.

## Code Breakdown:

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

## Expected Output: 
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

## Insights:

The dataset contains 953 rows and 24 columns, with each row representing a unique track and each column providing various details such as track names, artist information, musical attributes, release details, and streaming data. The columns include a mix of numerical (e.g., streams, artist_count, released_year, bpm, danceability_%, etc.) and categorical (e.g., track_name, artist(s)_name, key, mode) data types.

Regarding missing values, there are a few important observations. The streams column has one missing value for the track "Love Grows (Where My Rosemary Goes)", which has been intentionally set to NaN to ensure the accuracy of the analysis. Aside from this, there are missing values in the key (95 missing values) and in_shazam_charts (50 missing values) columns. These missing values are relatively sparse and suggest that some tracks might not have a defined key or lack data for the Shazam charts. 

--- 

## Basic Descriptive Statistics
1. **Streams Analysis**: 
   - Mean, median, and standard deviation for the `streams` column are calculated to understand central tendencies and dispersion in streaming counts.
2. **Released Year and Artist Count Distribution**: 
   - Analysis of the distribution of the `released_year` and `artist_count` columns.
   - Trends and outliers in release years and artist collaborations are identified.

## Problem(s):
- **Part A**: What are the mean, median, and standard deviation of the streams column?
- **Part B**: What is the distribution of released_year and artist_count? Are there any noticeable trends or outliers?

## Approach:

##### *Part A:*
Use summary statistics methods to get an overview of numerical columns and calculate specific metrics for `streams`.
- `{mean_streams}` – This represents the average number of streams across all tracks.
- `{median_streams}` – The median provides the midpoint of the streams data, less affected by outliers than the mean.
- `{std_streams}` – This measures the spread of stream counts, showing variability in track popularity.

##### *Part B:*
- Use histograms with kernel density estimates (KDE) to visualize the distribution of the release year and artist count.

## Functions to be Used:
##### *Part A:*
  - **`Function:`** `Spotify_Data.describe()`
    - **`Description:`** Generates summary statistics for the numerical columns in the `Spotify_Data` DataFrame, including count, mean, standard deviation, min, max, and percentiles.

  - **`Function:`** `Spotify_Data.describe().transpose()`
    - **`Description:`** Transposes the result of `describe()` to display the statistics in a more readable format, with columns as rows.

  - **`Function:`** `print("Summary Statistics for Numerical Columns:\n")`
    - **`Description:`** Prints a label "Summary Statistics for Numerical Columns" followed by a newline to introduce the summary statistics output.

  - **`Function:`** `print(Spotify_Data.describe().transpose())`
    - **`Description:`** Prints the summary statistics for the numerical columns in the `Spotify_Data` DataFrame, showing essential statistics like mean, standard deviation, etc.

  - **`Function:`** `print(f"{'-'*30}")`
    - **`Description:`** Prints a line of dashes (30 dashes) to visually separate sections of the output for better readability.

  - **`Function:`** `Spotify_Data['streams'].mean()`
    - **`Description:`** Calculates the mean (average) of the 'streams' column in the `Spotify_Data` DataFrame.

  - **`Function:`** `Spotify_Data['streams'].median()`
    - **`Description:`** Calculates the median of the 'streams' column in the `Spotify_Data` DataFrame, which represents the middle value when the data is ordered.

  - **`Function:`** `Spotify_Data['streams'].std()`
    - **`Description:`** Calculates the standard deviation of the 'streams' column in the `Spotify_Data` DataFrame, indicating how much the stream values deviate from the mean.

  - **`Function:`** `print("\nDetailed Statistics for 'Streams' Column:")`
    - **`Description:`** Prints a label "Detailed Statistics for 'Streams' Column" followed by a newline to introduce the specific statistics for the 'streams' column.

  - **`Function:`** `print("Mean streams:", mean_streams)`
    - **`Description:`** Prints the calculated mean of the 'streams' column.

  - **`Function:`** `print("Median streams:", median_streams)`
    - **`Description:`** Prints the calculated median of the 'streams' column.

  - **`Function:`** `print("Standard deviation of streams:", std_streams)`
    - **`Description:`** Prints the calculated standard deviation of the 'streams' column, giving insight into the spread of the data.

##### *Part B:*
  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for the histogram with a size of 10 by 6 inches.

  - **`Function:`** `sns.histplot(Spotify_Data['released_year'], bins=20, kde=True)`
    - **`Description:`** Creates a histogram with 20 bins for the 'released_year' column from `Spotify_Data`, and overlays a kernel density estimate (KDE) to show the distribution of release years.

  - **`Function:`** `plt.title('Distribution of Released Year')`
    - **`Description:`** Sets the title of the plot to "Distribution of Released Year."

  - **`Function:`** `plt.xlabel('Released Year')`
    - **`Description:`** Sets the label for the x-axis to "Released Year."

  - **`Function:`** `plt.ylabel('Count')`
    - **`Description:`** Sets the label for the y-axis to "Count," indicating the number of occurrences for each 'released_year'.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the plot for the 'released_year' distribution.

  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for the second histogram with a size of 10 by 6 inches.

  - **`Function:`** `sns.histplot(Spotify_Data['artist_count'], bins=20, kde=True)`
    - **`Description:`** Creates a histogram with 20 bins for the 'artist_count' column from `Spotify_Data`, and overlays a kernel density estimate (KDE) to show the distribution of the number of artists.

  - **`Function:`** `plt.title('Distribution of Artist Count')`
    - **`Description:`** Sets the title of the plot to "Distribution of Artist Count."

  - **`Function:`** `plt.xlabel('Artist Count')`
    - **`Description:`** Sets the label for the x-axis to "Artist Count."

  - **`Function:`** `plt.ylabel('Count')`
    - **`Description:`** Sets the label for the y-axis to "Count," indicating the number of occurrences for each 'artist_count'.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the plot for the 'artist_count' distribution.

## Code Breakdown:

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

## Expected Output:
- Summary statistics for all numerical columns, and the mean, median, and standard deviation for the `streams` column.
- Two histograms showing the distribution of the `released_year` and `artist_count`, helping to identify trends and potential outliers.

##### *Part A:*

![image](https://github.com/user-attachments/assets/2b139f95-7500-460a-9e09-275c1ae79a75)
![image](https://github.com/user-attachments/assets/d833ae44-701b-4eb9-96b8-00276e186ef0)

##### *Part B:*

##### **Distribution of Released Year**

![image](https://github.com/user-attachments/assets/1a8e0951-2afa-4bab-86c5-a820208d006b)

##### **Distribution of Artist Count**

![image](https://github.com/user-attachments/assets/9b9d685e-e8ab-4b48-877a-103390d0e1e4)


###### *Note: Only the `streams` column for "Love Grows (Where My Rosemary Goes)" is treated as `NaN`, ensuring other columns retain their original values.*

## Insights:
For the streams column, the mean number of streams is approximately 514,137,425, with a median of 290,530,915. The standard deviation is very high at approximately 566,856,949, indicating significant variability in the streams across the tracks. This suggests that while there are some tracks with extraordinarily high stream counts, many tracks have much lower stream numbers, which is typical in a dataset with a mix of popular and lesser-known tracks.

Regarding the released_year column, the majority of the tracks were released in recent years, specifically in the 2020s, as indicated by the median value of 2022 and the range from 1930 to 2023. This reflects a modern trend in the dataset, with the most significant number of tracks being released in the past decade. While, for artist_count, the mean is approximately 1.56, with most tracks featuring 1 or 2 artists (25th percentile: 1, 75th percentile: 2). The maximum value of 8 artists is an outlier compared to the majority of tracks that have fewer collaborators. This suggests that most tracks are single-artist, with a smaller proportion featuring multiple artists. In summary, the streams column exhibits high variability, while the released_year and artist_count distributions follow expected patterns, with recent years dominating and most tracks featuring one or two artists. 

---

## Top Performers

1. **Top Streamed Tracks**:
   - The track with the highest number of streams is identified.
   - A list of the top 5 most-streamed tracks is provided for further analysis.
2. **Most Frequent Artists**:
   - The top 5 most frequent artists, based on the number of tracks in the dataset, are displayed.

## Problem(s):
- **Part A**: Which track has the highest number of streams? Display the top 5 most streamed tracks.
- **Part B**: Who are the top 5 most frequent artists based on the number of tracks in the dataset?

## Approach:
- Find the top 5 most-streamed tracks by sorting the `streams` column, and identify the top 5 most frequent artists by counting the occurrences in the `artist(s)_name` column.

## Functions to be Used:
##### *Part A:*
  - **`Function:`** `Spotify_Data[['track_name', 'streams']]`
    - **`Description:`** Selects the 'track_name' and 'streams' columns from the `Spotify_Data` DataFrame to focus on these two attributes for further analysis.

  - **`Function:`** `.dropna()`
    - **`Description:`** Removes any rows that contain `NaN` (missing) values from the selected 'track_name' and 'streams' columns, ensuring only valid data is considered.

  - **`Function:`** `.sort_values(by='streams', ascending=False)`
    - **`Description:`** Sorts the data by the 'streams' column in descending order, ensuring the tracks with the highest streams appear at the top.

  - **`Function:`** `.head(5)`
    - **`Description:`** Selects the top 5 rows from the sorted DataFrame, which corresponds to the top 5 most streamed tracks.

  - **`Function:`** `print("The Top 5 Most Streamed Tracks in Spotify:\n")`
    - **`Description:`** Prints a label indicating the output of the top 5 most streamed tracks.

  - **`Function:`** `print(most_streamed, "\n")`
    - **`Description:`** Prints the `most_streamed` DataFrame, which contains the top 5 tracks by stream count.

  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for plotting with a size of 10 by 6 inches.

  - **`Function:`** `sns.barplot(x='streams', y='track_name', data=most_streamed, palette='coolwarm', hue='track_name')`
    - **`Description:`** Creates a horizontal bar plot for the 'streams' vs. 'track_name' columns from the `most_streamed` DataFrame. The `palette='coolwarm'` argument sets the color palette, and `hue='track_name'` differentiates the bars by track.

  - **`Function:`** `plt.title('Top 5 Most Streamed Tracks')`
    - **`Description:`** Sets the title of the plot to "Top 5 Most Streamed Tracks."

  - **`Function:`** `plt.xlabel('Streams')`
    - **`Description:`** Sets the label for the x-axis to "Streams," indicating the number of streams for each track.

  - **`Function:`** `plt.ylabel('Track Name')`
    - **`Description:`** Sets the label for the y-axis to "Track Name," displaying the names of the tracks.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the plot, allowing visualization of the top 5 most streamed tracks.

##### *Part B:*
  - **`Function:`** `Spotify_Data['artist(s)_name'].value_counts()`
    - **`Description:`** Counts the occurrences of each unique artist in the 'artist(s)_name' column of the `Spotify_Data` DataFrame, showing how many tracks each artist has in the dataset.

  - **`Function:`** `.head(5)`
    - **`Description:`** Selects the top 5 artists with the highest track counts from the `value_counts()` result.

  - **`Function:`** `print("The Top 5 Most Frequent Artists Based on Track Count:\n")`
    - **`Description:`** Prints a label indicating the output of the top 5 most frequent artists based on track count.

  - **`Function:`** `print(frequent_artists, "\n")`
    - **`Description:`** Prints the `frequent_artists` variable, which contains the top 5 artists by track count.

  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for plotting with a size of 10 by 6 inches.

  - **`Function:`** `plt.bar(frequent_artists.index, frequent_artists.values, color=plt.cm.Pastel1(range(len(frequent_artists))))`
    - **`Description:`** Creates a bar plot with the artist names as the x-axis (using `frequent_artists.index`) and the number of tracks as the y-axis (using `frequent_artists.values`). The `color=plt.cm.Pastel1(range(len(frequent_artists)))` argument applies a soft pastel color palette to the bars.

  - **`Function:`** `plt.title('The Top 5 Most Frequent Artists Based on Track Count')`
    - **`Description:`** Sets the title of the plot to "The Top 5 Most Frequent Artists Based on Track Count."

  - **`Function:`** `plt.xlabel('Artist(s) Name')`
    - **`Description:`** Sets the label for the x-axis to "Artist(s) Name."

  - **`Function:`** `plt.ylabel('Number of Tracks')`
    - **`Description:`** Sets the label for the y-axis to "Number of Tracks."

  - **`Function:`** `plt.xticks(rotation=45, ha='right')`
    - **`Description:`** Rotates the x-axis labels by 45 degrees for better readability, and aligns the labels to the right using `ha='right'`.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the plot, allowing visualization of the top 5 most frequent artists based on track count.

## Code Breakdown:

##### *Part A:*
```python
# Selects the 'track_name' and 'streams' columns, drops rows with NaN values in 'streams',
# sorts by streams in descending order, and selects the top 5 tracks.
most_streamed = Spotify_Data[['track_name', 'streams']].dropna().sort_values(by='streams', ascending=False).head(5)

# Initializes a figure with size 10x6 inches for the bar plot of top 5 most streamed tracks.
plt.figure(figsize=(10, 6))

# Creates a horizontal bar plot for 'streams' vs. 'track_name' with a coolwarm color palette.
sns.barplot(x='streams', y='track_name', data=most_streamed, palette='coolwarm', hue='track_name') 

# Sets the title of the plot to "Top 5 Most Streamed Tracks".
plt.title('Top 5 Most Streamed Tracks')

# Labels the x-axis as "Streams".
plt.xlabel('Streams')

# Labels the y-axis as "Track Name".
plt.ylabel('Track Name')

# Displays the bar plot for the top 5 most streamed tracks.
plt.show()
```

##### *Part B:*
```python
# Counts occurrences of each artist in the 'artist(s)_name' column, sorts in descending order, and selects the top 5.
frequent_artists = Spotify_Data['artist(s)_name'].value_counts().head(5)

# Prints the top 5 most frequent artists based on track count.
print("The Top 5 Most Frequent Artists Based on Track Count:\n")
print(frequent_artists, "\n")

# Initializes a figure with size 10x6 inches for the bar plot of top 5 most frequent artists.
plt.figure(figsize=(10, 6))

# Creates a bar plot with artist names on the x-axis and track counts on the y-axis, using a pastel color palette.
bars = plt.bar(frequent_artists.index, frequent_artists.values, color=plt.cm.Pastel1(range(len(frequent_artists))))

# Sets the title of the plot to "The Top 5 Most Frequent Artists Based on Track Count".
plt.title('The Top 5 Most Frequent Artists Based on Track Count')

# Labels the x-axis as "Artist(s) Name".
plt.xlabel('Artist(s) Name')

# Labels the y-axis as "Number of Tracks".
plt.ylabel('Number of Tracks')

# Rotates the x-axis labels by 45 degrees for improved readability.
plt.xticks(rotation=45, ha='right')

# Displays the bar plot for the top 5 most frequent artists.
plt.show()
```

## Expected Output:
- A list of the top 5 most-streamed tracks with a bar chart visualization and a list of the top 5 most frequent artists with a bar chart.

##### *Part A:*

![image](https://github.com/user-attachments/assets/a8ced73b-9c89-4638-9bc0-0e39ba41b526)

##### *Part B:*

![image](https://github.com/user-attachments/assets/6b7a0335-ae52-4adf-8ef3-f0fc43c8de6c)

## Insights:
The track with the highest number of streams in the dataset is "Blinding Lights" by The Weeknd, with a remarkable 3.7 billion streams. This song tops the list of the top 5 most streamed tracks, showcasing its global popularity and cultural impact. Following closely are Ed Sheeran’s "Shape of You" with 3.56 billion streams, and "Someone You Loved" by Lewis Capaldi, amassing 2.88 billion streams. Other notable mentions include "Dance Monkey" by Tones and I, with 2.86 billion streams, and "Sunflower" by Post Malone and Swae Lee from the *Spider-Man: Into the Spider-Verse* soundtrack, which has reached 2.8 billion streams. These songs reflect diverse genres and styles, highlighting the wide-reaching appeal of each track. Additionally, "Love Grows (Where My Rosemary Goes)" was found to have missing stream data, thus it did not appear in this ranking.

In terms of artist frequency, Taylor Swift leads the dataset with 34 tracks, underscoring her prolific output and consistent popularity across various album releases. The Weeknd follows with 22 tracks, reinforcing his widespread acclaim, particularly through his chart-topping singles. Bad Bunny and SZA each appear 19 times, showcasing their significant contributions to Latin and R&B genres, respectively. Finally, Harry Styles rounds out the top five with 17 tracks, reflecting his success as a solo artist after transitioning from One Direction. The prominence of these artists suggests that frequent releases from high-demand artists resonate with audiences, establishing a strong presence on streaming platforms and shaping music trends.

---

## Temporal Trends

1. **Tracks Released Over Time**:
   - Analysis of the number of tracks released per year. A line plot is created to show trends in annual releases.
2. **Monthly Release Patterns**:
   - Examination of release patterns by month to identify any seasonal trends.
   - Identification of the month with the highest number of track releases.

## Problem(s):
- **Part A**: Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year.
- **Part B**: Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?

## Approach:
- Count the number of tracks released per year and per month, and use line and bar plots to visualize the trends.

## Functions to be Used:

##### *Part A:*
  - **`Function:`** `Spotify_Data['released_year'].value_counts()`
    - **`Description:`** Counts the occurrences of each unique value in the 'released_year' column of the `Spotify_Data` DataFrame, indicating how many tracks were released in each year.

  - **`Function:`** `.sort_index()`
    - **`Description:`** Sorts the counted values by the index (year) in ascending order, ensuring the years are displayed chronologically.

  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for plotting with a size of 10 by 6 inches.

  - **`Function:`** `plt.plot(release_year_counts.index, release_year_counts.values, marker='o', color='skyblue', label=f'Peak Year: {release_year_counts.idxmax()}')`
    - **`Description:`** Creates a line plot with years on the x-axis (`release_year_counts.index`) and the number of tracks released in those years on the y-axis (`release_year_counts.values`). It uses circular markers ('o') and the color 'skyblue'. The `label` argument displays the peak release year on the legend.

  - **`Function:`** `plt.title('Number of Tracks Released Over Time', fontsize=16)`
    - **`Description:`** Sets the title of the plot to "Number of Tracks Released Over Time" with a font size of 16.

  - **`Function:`** `plt.xlabel('Year', fontsize=14)`
    - **`Description:`** Sets the label for the x-axis to "Year" with a font size of 14.

  - **`Function:`** `plt.ylabel('Number of Tracks', fontsize=14)`
    - **`Description:`** Sets the label for the y-axis to "Number of Tracks" with a font size of 14.

  - **`Function:`** `plt.grid(visible=True, linestyle='--', linewidth=0.5)`
    - **`Description:`** Displays a grid on the plot with dashed lines ('--') and a line width of 0.5 for better readability.

  - **`Function:`** `plt.legend(fontsize=12)`
    - **`Description:`** Displays the legend with a font size of 12. The legend shows the peak year information.

  - **`Function:`** `plt.tight_layout()`
    - **`Description:`** Adjusts the plot layout to ensure everything fits within the figure, avoiding clipping of labels or titles.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the plot, visualizing the number of tracks released over time.

##### *Part B:*
  - **`Function:`** `Spotify_Data['released_month'].value_counts()`
    - **`Description:`** Counts the occurrences of each unique month in the 'released_month' column of the `Spotify_Data` DataFrame, showing how many tracks were released in each month.

  - **`Function:`** `.sort_index()`
    - **`Description:`** Sorts the counted values by the month index (in chronological order from January to December).

  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for plotting with a size of 10 by 6 inches.

  - **`Function:`** `monthly_release_counts.plot(kind='bar', color='lightseagreen')`
    - **`Description:`** Creates a bar plot for the `monthly_release_counts` data, with bars colored 'lightseagreen' to represent the number of tracks released in each month.

  - **`Function:`** `plt.title('Number of Tracks Released Per Month', fontsize=16)`
    - **`Description:`** Sets the title of the plot to "Number of Tracks Released Per Month" with a font size of 16.

  - **`Function:`** `plt.xlabel('Month', fontsize=14)`
    - **`Description:`** Sets the label for the x-axis to "Month" with a font size of 14.

  - **`Function:`** `plt.ylabel('Number of Tracks', fontsize=14)`
    - **`Description:`** Sets the label for the y-axis to "Number of Tracks" with a font size of 14.

  - **`Function:`** `plt.xticks(ticks=range(12), labels=['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'], rotation=45)`
    - **`Description:`** Sets the x-axis ticks to represent each month (from January to December), with labels rotated by 45 degrees for readability.

  - **`Function:`** `plt.grid(visible=True, linestyle='--', linewidth=0.5)`
    - **`Description:`** Displays a grid on the plot with dashed lines ('--') and a line width of 0.5 for better readability.

  - **`Function:`** `monthly_release_counts.idxmax()`
    - **`Description:`** Finds the index (month) with the highest count of released tracks.

  - **`Function:`** `monthly_release_counts.max()`
    - **`Description:`** Returns the maximum value from `monthly_release_counts`, which is the number of tracks released in the peak month.

  - **`Function:`** `plt.legend([f'Most releases: {peak_month_name} ({peak_month_count} tracks)'], fontsize=12)`
    - **`Description:`** Displays the legend, highlighting the month with the most releases and the number of tracks released during that month.

  - **`Function:`** `plt.tight_layout()`
    - **`Description:`** Adjusts the plot layout to ensure that all elements fit within the figure and nothing is clipped.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the plot, visualizing the number of tracks released per month.

  - **`Function:`** `print(f"\nMonth with the most releases: {peak_month_name}")`
    - **`Description:`** Prints the month with the most releases.

  - **`Function:`** `print(f"Number of tracks released in that month: {peak_month_count}")`
    - **`Description:`** Prints the number of tracks released in the month with the highest number of releases.

## Code Breakdown:

##### *Part A:*
```python
# Counts occurrences of each release year, then sorts by year in ascending order.
release_year_counts = Spotify_Data['released_year'].value_counts().sort_index()

# Initializes a figure with size 10x6 inches for the line plot.
plt.figure(figsize=(10, 6))

# Plots the release year (x-axis) vs. number of tracks (y-axis), with a sky-blue line, markers, and peak year label.
plt.plot(release_year_counts.index, release_year_counts.values, marker='o', color='skyblue', label=f'Peak Year: {release_year_counts.idxmax()}')

# Sets the title of the plot to "Number of Tracks Released Over Time" and customizes font size.
plt.title('Number of Tracks Released Over Time', fontsize=16)

# Labels the x-axis as "Year" with a font size of 14.
plt.xlabel('Year', fontsize=14)

# Labels the y-axis as "Number of Tracks" with a font size of 14.
plt.ylabel('Number of Tracks', fontsize=14)

# Adds a dashed grid to the plot with a line width of 0.5 for better readability.
plt.grid(visible=True, linestyle='--', linewidth=0.5)

# Displays a legend to label the peak year in the plot.
plt.legend(fontsize=12)

# Adjusts the layout to prevent overlapping elements and improve visual alignment.
plt.tight_layout()

# Displays the line plot showing the number of tracks released over time.
plt.show()
```

##### *Part B:*
```python
# Counts occurrences of each release month, then sorts by month in ascending order.
monthly_release_counts = Spotify_Data['released_month'].value_counts().sort_index()

# Initializes a figure with size 10x6 inches for the bar plot.
plt.figure(figsize=(10, 6))

# Plots the monthly release counts as a bar chart with a lightseagreen color for bars.
monthly_release_counts.plot(kind='bar', color='lightseagreen')

# Sets the title of the plot to "Number of Tracks Released Per Month" and customizes font size.
plt.title('Number of Tracks Released Per Month', fontsize=16)

# Labels the x-axis as "Month" with a font size of 14.
plt.xlabel('Month', fontsize=14)

# Labels the y-axis as "Number of Tracks" with a font size of 14.
plt.ylabel('Number of Tracks', fontsize=14)

# Sets custom x-axis tick labels for each month and rotates them by 45 degrees for readability.
plt.xticks(ticks=range(12), labels=['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'], rotation=45)

# Adds a dashed grid to the plot with a line width of 0.5 for better readability.
plt.grid(visible=True, linestyle='--', linewidth=0.5)

# Finds the month with the highest number of releases and stores it as `peak_month`.
peak_month = monthly_release_counts.idxmax()

# Maps the numeric month index to the month name and gets the release count for that month.
peak_month_name = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'][peak_month - 1]
peak_month_count = monthly_release_counts.max()

# Displays a legend with the name and release count of the month with the most releases.
plt.legend([f'Most releases: {peak_month_name} ({peak_month_count} tracks)'], fontsize=12)

# Adjusts the layout to prevent overlapping elements and improve visual alignment.
plt.tight_layout()

# Displays the bar plot showing the number of tracks released per month.
plt.show()

# Prints the month name and track count for the month with the most releases.
print(f"\nMonth with the most releases: {peak_month_name}")
print(f"Number of tracks released in that month: {peak_month_count}")
```

## Expected Output:
- Line plot showing the number of tracks released each year and a bar plot showing monthly release trends with labels for the peak release year and month.

##### *Part A:*

![image](https://github.com/user-attachments/assets/b5ca40c9-f651-438c-88d4-b5f889aee148)

##### *Part B:*

![image](https://github.com/user-attachments/assets/b1dcee0d-08d2-4853-ba27-91393ac10a55)

```python
Month with the most releases: Jan
Number of tracks released in that month: 134
```

## Insights:
The number of tracks released over time shows a significant upward trend, especially in recent years. As seen in the plot, the number of tracks remained relatively low and stable from the 1930s to around the 2000s, with only small fluctuations. However, starting in the 2010s, there was a noticeable increase, reaching a peak in 2022 with over 400 tracks released, marking it as the most prolific year in the dataset. This spike in recent years could reflect the ease of digital music distribution and streaming platforms, making it simpler for artists to release music more frequently and reach larger audiences.

When examining the monthly release patterns, January stands out as the month with the most track releases, totaling 134 tracks. This suggests that the start of the year might be a popular time for new releases, possibly due to strategic timing, as artists and record labels aim to capture listener interest after the holiday season. Overall, while annual releases have grown dramatically, there seems to be a particular emphasis on releasing music at the beginning of the calendar year.

---

## Genre and Music Characteristics

1. **Correlation Analysis**:
   - Examining the relationship between `streams` and attributes like `bpm`, `danceability_%`, and `energy_%`.
   - Insights into which attributes most influence track popularity.
2. **Danceability and Energy Relationship**:
   - Correlation between `danceability_%` and `energy_%` as well as between `valence_%` and `acousticness_%`.

## Problem(s):
- **Part A**: Examine the correlation between streams and musical attributes like bpm, danceability_%, and energy_%. Which attributes seem to influence streams the most?
- **Part B**: Is there a correlation between danceability_% and energy_%? How about valence_% and acousticness_%?

## Approach:
##### *Part A:*
- Use correlation analysis with `pandas` and `seaborn` to calculate and visualize the relationship between `streams` and each musical attribute (bpm, danceability, energy).

##### *Part B:*
- Calculate the correlation between danceability_% and energy_%, and between valence_% and acousticness_%, followed by side-by-side scatter plots with regression lines to visualize these relationships. The regression lines will help identify any linear correlations between the variables.

## Functions to be Used:

##### *Part A:*
  - **`Function:`** `Spotify_Data[['streams', 'bpm', 'danceability_%', 'energy_%']].corr()`
    - **`Description:`** Computes the correlation matrix for the selected columns ('streams', 'bpm', 'danceability_%', 'energy_%') in the `Spotify_Data` DataFrame. This matrix shows the linear relationship between the variables.

  - **`Function:`** `print("Correlation matrix:\n")`
    - **`Description:`** Prints a header text indicating that the correlation matrix will be displayed.

  - **`Function:`** `print(correlation_matrix, "\n")`
    - **`Description:`** Prints the correlation matrix to the console, showing the relationships between the selected musical attributes and the 'streams' column.

  - **`Function:`** `plt.figure(figsize=(8, 6))`
    - **`Description:`** Initializes a new figure for plotting with a size of 8 by 6 inches.

  - **`Function:`** `sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', vmin=-1, vmax=1)`
    - **`Description:`** Creates a heatmap to visualize the correlation matrix. The `annot=True` argument displays the numerical values in the cells, `cmap='coolwarm'` sets the color palette, and `vmin=-1` and `vmax=1` specify the range of correlation values, from -1 (strong negative correlation) to 1 (strong positive correlation).

  - **`Function:`** `plt.title('Correlation between Streams and Musical Attributes')`
    - **`Description:`** Sets the title of the heatmap to "Correlation between Streams and Musical Attributes".

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the heatmap plot to visualize the correlation matrix.
  
##### *Part B:*
  - **`Function:`** `Spotify_Data['danceability_%'].corr(Spotify_Data['energy_%'])`
    - **`Description:`** Computes the Pearson correlation between the 'danceability_%' and 'energy_%' columns in the `Spotify_Data` DataFrame, showing the linear relationship between danceability and energy.

  - **`Function:`** `print(f"Correlation between Danceability and Energy: {dance_energy_corr:.2f}")`
    - **`Description:`** Prints the correlation between danceability and energy, formatted to two decimal places.

  - **`Function:`** `Spotify_Data['valence_%'].corr(Spotify_Data['acousticness_%'])`
    - **`Description:`** Computes the Pearson correlation between the 'valence_%' and 'acousticness_%' columns in the `Spotify_Data` DataFrame, indicating the linear relationship between valence and acousticness.

  - **`Function:`** `print(f"Correlation between Valence and Acousticness: {valence_acoustic_corr:.2f}")`
    - **`Description:`** Prints the correlation between valence and acousticness, formatted to two decimal places.

  - **`Function:`** `plt.subplots(1, 2, figsize=(18, 8))`
    - **`Description:`** Creates a figure with two subplots (1 row, 2 columns) and specifies the figure size of 18 by 8 inches.

  - **`Function:`** `sns.regplot(x='danceability_%', y='energy_%', data=Spotify_Data, scatter_kws={'s': 50, 'alpha': 0.5, 'color': 'darkblue'}, line_kws={'color': 'red', 'linewidth': 2}, ax=axes[0])`
    - **`Description:`** Creates a scatter plot with a regression line for 'danceability_%' vs 'energy_%'. The `scatter_kws` argument customizes the scatter plot (size, transparency, color), and the `line_kws` argument customizes the regression line (color and width). This plot is placed in the first subplot (`axes[0]`).

  - **`Function:`** `axes[0].set_title('Danceability vs Energy', fontsize=18)`
    - **`Description:`** Sets the title for the first subplot as 'Danceability vs Energy' with a font size of 18.

  - **`Function:`** `axes[0].set_xlabel('Danceability (%)', fontsize=14)`
    - **`Description:`** Labels the x-axis of the first subplot as 'Danceability (%)' with a font size of 14.

  - **`Function:`** `axes[0].set_ylabel('Energy (%)', fontsize=14)`
    - **`Description:`** Labels the y-axis of the first subplot as 'Energy (%)' with a font size of 14.

  - **`Function:`** `axes[0].grid(True, linestyle='--', linewidth=0.7, alpha=0.5)`
    - **`Description:`** Adds a grid to the first subplot with dashed lines, line width of 0.7, and alpha transparency of 0.5.

  - **`Function:`** `sns.regplot(x='valence_%', y='acousticness_%', data=Spotify_Data, scatter_kws={'s': 50, 'alpha': 0.5, 'color': 'darkgreen'}, line_kws={'color': 'orange', 'linewidth': 2}, ax=axes[1])`
    - **`Description:`** Creates a scatter plot with a regression line for 'valence_%' vs 'acousticness_%'. Customizes the scatter and line properties, placing the plot in the second subplot (`axes[1]`).

  - **`Function:`** `axes[1].set_title('Valence vs Acousticness', fontsize=18)`
    - **`Description:`** Sets the title for the second subplot as 'Valence vs Acousticness' with a font size of 18.

  - **`Function:`** `axes[1].set_xlabel('Valence (%)', fontsize=14)`
    - **`Description:`** Labels the x-axis of the second subplot as 'Valence (%)' with a font size of 14.

  - **`Function:`** `axes[1].set_ylabel('Acousticness (%)', fontsize=14)`
    - **`Description:`** Labels the y-axis of the second subplot as 'Acousticness (%)' with a font size of 14.

  - **`Function:`** `axes[1].grid(True, linestyle='--', linewidth=0.7, alpha=0.5)`
    - **`Description:`** Adds a grid to the second subplot with dashed lines, line width of 0.7, and alpha transparency of 0.5.

  - **`Function:`** `plt.tight_layout()`
    - **`Description:`** Adjusts the layout to ensure that subplots fit within the figure area without overlapping.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the figure containing both scatter plots with regression lines.

## Code Breakdown:

##### *Part A:*
```python
# Calculates the correlation matrix between 'streams', 'bpm', 'danceability_%', and 'energy_%' columns.
correlation_matrix = Spotify_Data[['streams', 'bpm', 'danceability_%', 'energy_%']].corr()

# Prints the correlation matrix to the console.
print("Correlation matrix:\n")
print(correlation_matrix, "\n")

# Initializes a figure with size 8x6 inches for the heatmap.
plt.figure(figsize=(8, 6))

# Creates a heatmap to visualize the correlation matrix with annotations, using a coolwarm color palette.
# Sets the color scale range from -1 to 1 to align with correlation coefficient values.
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', vmin=-1, vmax=1)

# Sets the title of the heatmap plot to "Correlation between Streams and Musical Attributes".
plt.title('Correlation between Streams and Musical Attributes')

# Displays the heatmap plot.
plt.show()
```

##### *Part B:*
```python
# Calculates the correlation between 'danceability_%' and 'energy_%' columns.
dance_energy_corr = Spotify_Data['danceability_%'].corr(Spotify_Data['energy_%'])

# Prints the correlation coefficient between Danceability and Energy, formatted to two decimal places.
print(f"Correlation between Danceability and Energy: {dance_energy_corr:.2f}")

# Calculates the correlation between 'valence_%' and 'acousticness_%' columns.
valence_acoustic_corr = Spotify_Data['valence_%'].corr(Spotify_Data['acousticness_%'])

# Prints the correlation coefficient between Valence and Acousticness, formatted to two decimal places.
print(f"Correlation between Valence and Acousticness: {valence_acoustic_corr:.2f}")

# Initializes a side-by-side subplot with 1 row and 2 columns for scatter plots.
fig, axes = plt.subplots(1, 2, figsize=(18, 8))

# Creates a scatter plot with a regression line for Danceability vs Energy.
# Sets custom color, size, and transparency for scatter points, and style for the regression line.
sns.regplot(x='danceability_%', y='energy_%', data=Spotify_Data, 
            scatter_kws={'s': 50, 'alpha': 0.5, 'color': 'darkblue'}, 
            line_kws={'color': 'red', 'linewidth': 2}, ax=axes[0])

# Sets the title, x-axis label, and y-axis label for the Danceability vs Energy scatter plot.
axes[0].set_title('Danceability vs Energy', fontsize=18)
axes[0].set_xlabel('Danceability (%)', fontsize=14)
axes[0].set_ylabel('Energy (%)', fontsize=14)

# Adds a grid to the first plot with a dashed line style and adjusts transparency and line width.
axes[0].grid(True, linestyle='--', linewidth=0.7, alpha=0.5)

# Creates a scatter plot with a regression line for Valence vs Acousticness.
# Sets custom color, size, and transparency for scatter points, and style for the regression line.
sns.regplot(x='valence_%', y='acousticness_%', data=Spotify_Data, 
            scatter_kws={'s': 50, 'alpha': 0.5, 'color': 'darkgreen'}, 
            line_kws={'color': 'orange', 'linewidth': 2}, ax=axes[1])

# Sets the title, x-axis label, and y-axis label for the Valence vs Acousticness scatter plot.
axes[1].set_title('Valence vs Acousticness', fontsize=18)
axes[1].set_xlabel('Valence (%)', fontsize=14)
axes[1].set_ylabel('Acousticness (%)', fontsize=14)

# Adds a grid to the second plot with a dashed line style and adjusts transparency and line width.
axes[1].grid(True, linestyle='--', linewidth=0.7, alpha=0.5)

# Adjusts the layout to make the plots fit nicely within the figure area.
plt.tight_layout()

# Displays the scatter plots side by side.
plt.show()
```

## Expected Output:

##### *Part A:*

![image](https://github.com/user-attachments/assets/eba61b48-30d9-45c7-be94-4aa7d4c7ca81)

##### *Part B:*

![image](https://github.com/user-attachments/assets/b4577cd4-622d-42c3-80f4-5e1d1833618c)

## Insights:
Analyzing the correlation between streams and various musical attributes, it appears that none of the attributes, including bpm, danceability_%, and energy_%, show a strong influence on streaming numbers. The correlation coefficients for these attributes with streams are all close to zero, with danceability_% having the highest (though still weak) negative correlation of -0.11. This suggests that these musical features do not significantly impact a song's popularity on streaming platforms. The low correlations imply that other factors, such as artist popularity, marketing, or playlist placement, may play a more substantial role in driving streams.

When looking at the relationship between danceability_% and energy_%, there is a mild positive correlation of 0.20, indicating that tracks with higher energy tend to be slightly more danceable, though the relationship is not particularly strong. On the other hand, valence_% and acousticness_% show a weak negative correlation of -0.08, suggesting that acoustic tracks tend to be slightly less cheerful or "positive" in tone, but this relationship is also minimal. Overall, while there are some minor correlations, these attributes do not exhibit strong dependencies on each other, nor do they have a significant impact on streaming performance.

---

## Platform Popularity

1. **Platform Comparison**:
   - Comparison of track counts across platforms (`spotify_playlists`, `spotify_charts`, and `apple_playlists`).
   - Determination of which platform tends to favor popular tracks.

## Problem(s):
- How do the numbers of tracks in spotify_playlists, spotify_charts, and apple_playlists compare? Which platform seems to favor the most popular tracks?

## Approach:
##### *Part A:*
  - Compute the total number of tracks listed in playlists for each platform (Spotify, Deezer, and Apple).
  - Calculate the average streams for each platform by grouping the data based on tracks listed on each platform's playlists.
  - Visualize the results using bar charts: one to show the track counts for each platform, and another to check which platform 

##### *Part B:*
  - Reshape the data using `melt()` to focus on tracks in the playlists of each platform.
  - Use a boxplot to show the distribution of streams across platforms, revealing which platform has higher or lower average streams for the tracks.

## Functions to be Used:

##### *Part A:*
  - **`Function:`** `Spotify_Data['in_spotify_playlists'].sum()`
    - **`Description:`** Calculates the total count of tracks appearing in Spotify playlists by summing the values in the 'in_spotify_playlists' column.

  - **`Function:`** `Spotify_Data['in_deezer_playlists'].sum()`
    - **`Description:`** Calculates the total count of tracks appearing in Deezer playlists by summing the values in the 'in_deezer_playlists' column.

  - **`Function:`** `Spotify_Data['in_apple_playlists'].sum()`
    - **`Description:`** Calculates the total count of tracks appearing in Apple playlists by summing the values in the 'in_apple_playlists' column.

  - **`Function:`** `print("Number of Tracks in Each Platform's Playlist:")`
    - **`Description:`** Displays a label for the output of the platform counts.

  - **`Function:`** `print(platform_counts, "\n")`
    - **`Description:`** Prints the dictionary `platform_counts`, showing the number of tracks on each platform's playlist, followed by a newline for spacing.

  - **`Function:`** `Spotify_Data.groupby(['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists'])['streams'].mean()`
    - **`Description:`** Groups the data by whether a track appears on each platform’s playlist and calculates the mean number of streams for each group.

  - **`Function:`** `print("\nMean Streams Per Platform:\n", mean_streams_per_platform, "\n")`
    - **`Description:`** Prints a label and the mean streams for each platform group, followed by newlines for spacing.

  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for the bar chart with a size of 10 by 6 inches.

  - **`Function:`** `plt.bar(platform_counts.keys(), platform_counts.values(), color=['#1DB954', '#FF0000', '#A2AAAD'])`
    - **`Description:`** Creates a bar chart with platform names as labels (x-axis) and track counts as values (y-axis), using specified colors for each bar.

  - **`Function:`** `plt.title("Number of Tracks Listed on Each Platform's Playlist", fontsize=14, fontweight='bold')`
    - **`Description:`** Sets the title of the bar chart with font size 14 and bold font weight.

  - **`Function:`** `plt.xlabel("Platform", fontsize=12)`
    - **`Description:`** Sets the x-axis label to 'Platform' with font size 12.

  - **`Function:`** `plt.ylabel("Number of Tracks", fontsize=12)`
    - **`Description:`** Sets the y-axis label to 'Number of Tracks' with font size 12.

  - **`Function:`** `plt.text(bar.get_x() + bar.get_width() / 2, yval + 5, int(yval), ha='center', va='bottom', fontsize=12)`
    - **`Description:`** Adds the track count on top of each bar in the chart for better readability.
      - **`bar.get_x() + bar.get_width() / 2`** – Centers the text horizontally on top of each bar.
      - **`yval + 5`** – Positions the text slightly above the bar.
      - **`int(yval)`** – Converts the track count value to an integer.
      - **`ha='center'`** and **`va='bottom'`** – Aligns the text horizontally centered and vertically at the bottom.
      - **`fontsize=12`** – Sets font size of the text to 12.

  - **`Function:`** `plt.grid(True, axis='y', linestyle='--', alpha=0.7)`
    - **`Description:`** Adds a horizontal grid to the plot, with a dashed line style and adjusted transparency.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the bar chart.


##### *Part B:*
  - **`Function:`** `Spotify_Data.melt(id_vars=['streams'], value_vars=['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists'], var_name='Platform', value_name='In_Playlist')`
    - **`Description:`** Converts `Spotify_Data` into long-form format, keeping 'streams' as an identifier variable and transforming the playlist columns ('in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists') into a new variable named 'Platform' with the corresponding values under 'In_Playlist'.

  - **`Function:`** `plt.figure(figsize=(10, 6))`
    - **`Description:`** Initializes a new figure for the box plot with a size of 10 by 6 inches.

  - **`Function:`** `sns.boxplot(x='Platform', y='streams', data=melted_data, hue='Platform', palette='Set3')`
    - **`Description:`** Creates a box plot to visualize the distribution of 'streams' across different 'Platform' values, with color variation for each platform using the 'Set3' color palette.

  - **`Function:`** `plt.title('Distribution of Streams per Platform', fontsize=16)`
    - **`Description:`** Sets the title of the box plot to 'Distribution of Streams per Platform' with font size 16.

  - **`Function:`** `plt.xlabel('Platform', fontsize=14)`
    - **`Description:`** Sets the x-axis label to 'Platform' with font size 14.

  - **`Function:`** `plt.ylabel('Streams', fontsize=14)`
    - **`Description:`** Sets the y-axis label to 'Streams' with font size 14.

  - **`Function:`** `plt.grid(visible=True, linestyle='--', linewidth=0.5)`
    - **`Description:`** Adds a visible grid to the plot with dashed lines and a line width of 0.5 for better readability.

  - **`Function:`** `plt.tight_layout()`
    - **`Description:`** Adjusts the layout to ensure the plot fits within the figure space without overlapping elements.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the box plot.

## Code Breakdown:

##### *Part A:*
```python
# Count the number of tracks appearing on each platform's playlist
platform_counts = {
    'Spotify': Spotify_Data['in_spotify_playlists'].sum(),  # Counts tracks in Spotify playlists by summing boolean values.
    'Deezer': Spotify_Data['in_deezer_playlists'].sum(),    # Counts tracks in Deezer playlists by summing boolean values.
    'Apple': Spotify_Data['in_apple_playlists'].sum()       # Counts tracks in Apple playlists by summing boolean values.
}

# Display the counts
print("Number of Tracks in Each Platform's Playlist:")  # Prints a header to describe the upcoming data output.
print(platform_counts, "\n")  # Displays the dictionary with track counts for each platform.

# To check which platform favors the most popular tracks, calculate mean streams for each platform combination
mean_streams_per_platform = Spotify_Data.groupby(['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists'])['streams'].mean()
# Groups data by playlist inclusion across platforms and calculates the mean 'streams' for each combination.

# Display the mean streams per platform
print("\nMean Streams Per Platform:\n", mean_streams_per_platform, "\n")  # Prints the mean streams for each platform grouping.

# Plot a bar chart to visualize the track counts for each platform
plt.figure(figsize=(10, 6))  # Initializes a figure with dimensions 10x6 inches.
bars = plt.bar(platform_counts.keys(), platform_counts.values(), color=['#1DB954', '#FF0000', '#A2AAAD'])
# Plots a bar chart where each platform is a category, with platform colors representing Spotify, Deezer, and Apple.

# Adding grid, title, and labels
plt.title("Number of Tracks Listed on Each Platform's Playlist", fontsize=14, fontweight='bold')  # Sets the title with bold font.
plt.xlabel("Platform", fontsize=12)  # Labels the x-axis as "Platform" with font size 12.
plt.ylabel("Number of Tracks", fontsize=12)  # Labels the y-axis as "Number of Tracks" with font size 12.

# Add exact values on top of each bar for better readability
for bar in bars:
    yval = bar.get_height()  # Gets the height of each bar to position the text.
    plt.text(bar.get_x() + bar.get_width() / 2, yval + 5, int(yval), ha='center', va='bottom', fontsize=12)
    # Places the count value above each bar, centered and slightly above the top, with font size 12.

# Display grid for better readability
plt.grid(True, axis='y', linestyle='--', alpha=0.7)  # Adds a dashed horizontal grid with transparency for readability.

# Show the plot
plt.show()  # Displays the bar chart.
```

##### *Part B:*
```python
import pandas as pd      # Imports the pandas library for data manipulation.
import seaborn as sns    # Imports the seaborn library for advanced data visualization.
import matplotlib.pyplot as plt  # Imports matplotlib for plotting.

# Calculate the correlation matrix for 'streams', 'bpm', 'danceability_%', and 'energy_%' columns.
correlation_matrix = Spotify_Data[['streams', 'bpm', 'danceability_%', 'energy_%']].corr()

# Print the correlation matrix to the console.
print("Correlation matrix:\n")  # Prints a header to identify the correlation matrix output.
print(correlation_matrix, "\n")  # Displays the correlation matrix.

# Plot the correlation heatmap.
plt.figure(figsize=(8, 6))  # Initializes a figure with dimensions 8x6 inches.
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', vmin=-1, vmax=1)  # Creates a heatmap with annotations and a coolwarm color palette.
plt.title('Correlation between Streams and Musical Attributes')  # Sets the title of the heatmap.
plt.show()  # Displays the heatmap plot.

# Melt the DataFrame to long-form for plotting.
melted_data = Spotify_Data.melt(id_vars=['streams'], 
                                value_vars=['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists'], 
                                var_name='Platform', value_name='In_Playlist')
# Melts the DataFrame by keeping 'streams' as an identifier and converting playlist columns into a single 'Platform' column.
# 'In_Playlist' contains boolean values indicating if a song is in a specific playlist.

# Plotting the boxplot with hue to show distribution of streams per platform.
plt.figure(figsize=(10, 6))  # Initializes a new figure with dimensions 10x6 inches for the boxplot.
sns.boxplot(x='Platform', y='streams', data=melted_data, hue='Platform', palette='Set3')  # Creates a box plot for 'streams' distribution by platform.
plt.title('Distribution of Streams per Platform', fontsize=16)  # Sets the title for the boxplot with font size 16.
plt.xlabel('Platform', fontsize=14)  # Labels the x-axis as 'Platform' with font size 14.
plt.ylabel('Streams', fontsize=14)  # Labels the y-axis as 'Streams' with font size 14.
plt.grid(visible=True, linestyle='--', linewidth=0.5)  # Adds a dashed grid for improved readability.

# Show the box plot.
plt.tight_layout()  # Adjusts the plot layout to prevent overlapping elements.
plt.show()  # Displays the box plot.
```

## Expected Output:

##### *Part A:*

![image](https://github.com/user-attachments/assets/b7e03bd1-5646-4eeb-9ce0-6333f295a22c)

##### *Part B:*

![image](https://github.com/user-attachments/assets/88652c74-a605-45ce-91e1-eb645638715d)


---

## Advanced Analysis

1. **Key and Mode Patterns**:
   - Analysis of streaming patterns among tracks with similar `key` or `mode` (Major vs. Minor).
2. **Genres and Artists in Playlists/Charts**:
   - Identification of genres or artists that appear most frequently in playlists or charts.
   - Comparison of frequently appearing artists across platforms to determine platform-specific preferences.

## Problem(s):
- **Part A**: Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?
- **Part B**: Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.

## Approach:
##### *Part A:* 
  - The dataset is grouped by both 'key' and 'mode' (Major vs. Minor), calculating two metrics:
    - The **average streams** for each combination of key and mode.
    - The **track count** for each key and mode group, which represents how many tracks fall under each category.
  - Two subplots are created to visualize the relationships:
    1. A **bar plot for average streams** by key and mode.
    2. A **bar plot for track counts** by key and mode.
  - The first plot uses the 'viridis' color palette, while the second uses the 'coolwarm' palette to distinguish between the two metrics visually.

##### *Part A.1:*
  - The dataset is grouped by the 'key' column to calculate the average streams for each key.
  - The keys are then converted to strings for better readability when plotting.
  - A bar plot is created using the `seaborn` library to visualize the average streams for each key, with the colors of the bars representing different keys. The `viridis` color palette is used to differentiate the keys in the plot.
  - The plot includes the 'key' on the x-axis and 'average streams' on the y-axis, with the hue parameter applied to show the different keys with distinct colors.
  - The legend is hidden since the hue is just for color differentiation and not necessary for understanding the chart.

##### *Part A.2:*
  - The dataset is grouped by the 'mode' column, where `0` represents Minor and `1` represents Major, to calculate the average streams for each mode.
  - A bar plot is created using the `seaborn` library to visualize the average streams for each mode, with color applied using the `coolwarm` color palette to distinguish between Major and Minor.
  - The x-axis displays the mode (Minor or Major), and the y-axis shows the average streams.
  - The legend is hidden since the hue only adds color and doesn't provide additional meaningful information.

##### *Part B:*
- The data is grouped by artist and platform, and the total number of appearances for each artist is computed. Artists are then sorted based on their total appearances across all platforms in descending order. A bar chart is used to visualize the total appearances, where each bar represents the total appearances of each artist across all platforms. Missing values for artists that do not appear on certain platforms are treated as zero. The final results are displayed in a clear, readable table format.

## Functions to be Used:

##### *Part A:*
  - **`Function:`** `Spotify_Data.groupby(['key', 'mode']).agg()`
    - **`Description:`** Groups the `Spotify_Data` DataFrame by 'key' and 'mode' (Major vs Minor), then aggregates the data by calculating the average of 'streams' and the count of 'streams' to get track counts for each group. The aggregation is reset into a new DataFrame.

  - **`Function:`** `print("Patterns based on key and mode:")`
    - **`Description:`** Prints a message indicating that the patterns based on 'key' and 'mode' are about to be displayed.

  - **`Function:`** `print(key_mode_streams, "\n")`
    - **`Description:`** Prints the `key_mode_streams` DataFrame, which contains the calculated average streams and track count for each 'key' and 'mode' combination.

  - **`Function:`** `plt.figure(figsize=(12, 6))`
    - **`Description:`** Creates a new figure with the specified size of 12 inches by 6 inches to display the plots.

  - **`Function:`** `plt.subplot(1, 2, 1)`
    - **`Description:`** Creates the first subplot (1 row, 2 columns) for plotting the average streams by 'key' and 'mode'.

  - **`Function:`** `sns.barplot(x='key', y='streams', hue='mode', data=key_mode_streams, palette='viridis')`
    - **`Description:`** Creates a bar plot that shows the average streams by 'key' and 'mode' using the 'viridis' color palette. The 'hue' parameter allows the bars to be color-coded by the 'mode' (Major/Minor).

  - **`Function:`** `plt.title('Average Streams by Key and Mode')`
    - **`Description:`** Adds a title to the first subplot indicating that the plot shows the average streams by 'key' and 'mode'.

  - **`Function:`** `plt.xlabel('Key')`
    - **`Description:`** Labels the x-axis of the first subplot as 'Key'.

  - **`Function:`** `plt.ylabel('Average Streams')`
    - **`Description:`** Labels the y-axis of the first subplot as 'Average Streams'.

  - **`Function:`** `plt.subplot(1, 2, 2)`
    - **`Description:`** Creates the second subplot (1 row, 2 columns) for plotting the track count by 'key' and 'mode'.

  - **`Function:`** `sns.barplot(x='key', y='track_count', hue='mode', data=key_mode_streams, palette='coolwarm')`
    - **`Description:`** Creates a bar plot that shows the track count by 'key' and 'mode' using the 'coolwarm' color palette. The 'hue' parameter color-codes the bars by the 'mode' (Major/Minor).

  - **`Function:`** `plt.title('Track Count by Key and Mode')`
    - **`Description:`** Adds a title to the second subplot indicating that the plot shows the track count by 'key' and 'mode'.

  - **`Function:`** `plt.xlabel('Key')`
    - **`Description:`** Labels the x-axis of the second subplot as 'Key'.

  - **`Function:`** `plt.ylabel('Track Count')`
    - **`Description:`** Labels the y-axis of the second subplot as 'Track Count'.

  - **`Function:`** `plt.tight_layout()`
    - **`Description:`** Adjusts the layout of the subplots to ensure they fit well within the figure without overlap.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the final figure containing both the bar plots for average streams and track count by 'key' and 'mode'.

##### *Part A.1: 
  - **`Function:`** `import matplotlib.pyplot as plt`
    - **`Description:`** Imports the `matplotlib.pyplot` module, which is used for creating plots and visualizations.

  - **`Function:`** `import seaborn as sns`
    - **`Description:`** Imports the `seaborn` library, which provides a high-level interface for drawing attractive statistical graphics.

  - **`Function:`** `Spotify_Data.groupby('key')['streams'].mean()`
    - **`Description:`** Groups the `Spotify_Data` DataFrame by the 'key' column and calculates the mean of 'streams' for each group, providing the average streams per musical key.

  - **`Function:`** `plot_data = avg_streams_by_key.reset_index()`
    - **`Description:`** Resets the index of the `avg_streams_by_key` Series, converting it into a DataFrame, and makes 'key' a regular column instead of the index.

  - **`Function:`** `plot_data['key'] = plot_data['key'].astype(str)`
    - **`Description:`** Converts the 'key' column of `plot_data` to a string data type for better display and plotting purposes.

  - **`Function:`** `plt.figure(figsize=(10, 8))`
    - **`Description:`** Creates a new figure for plotting with a specified size of 10 inches by 8 inches.

  - **`Function:`** `sns.barplot(data=plot_data, x='key', y='streams', palette='viridis', hue='key', dodge=False)`
    - **`Description:`** Creates a bar plot using Seaborn, where the x-axis represents 'key', the y-axis represents the average 'streams', and the bars are color-coded by 'key' using the 'viridis' color palette. The `hue='key'` argument ensures that each key is color-coded uniquely, while `dodge=False` ensures the bars are not separated by the hue categories.

  - **`Function:`** `plt.xlabel('Musical Key')`
    - **`Description:`** Adds the label "Musical Key" to the x-axis of the plot.

  - **`Function:`** `plt.ylabel('Average Streams')`
    - **`Description:`** Adds the label "Average Streams" to the y-axis of the plot.

  - **`Function:`** `plt.title('Average Streams by Musical Key')`
    - **`Description:`** Sets the title of the plot to "Average Streams by Musical Key".

  - **`Function:`** `plt.legend([], [], frameon=False)`
    - **`Description:`** Hides the legend in the plot by passing empty lists for the legend handles and labels and setting `frameon=False` to avoid displaying a legend box.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the final plot on the screen after all adjustments and customizations.

##### *Part A.2:
  - **`Function:`** `Spotify_Data.groupby('mode')['streams'].mean().reset_index()`
    - **`Description:`** Groups the `Spotify_Data` DataFrame by the 'mode' column (Major vs Minor) and calculates the average of 'streams' for each group. It then resets the index to turn the result into a DataFrame.

  - **`Function:`** `plt.figure(figsize=(10, 8))`
    - **`Description:`** Creates a new figure for plotting with a specified size of 10 inches by 8 inches.

  - **`Function:`** `sns.barplot(data=avg_streams_by_mode, x='mode', y='streams', palette='coolwarm', hue='mode', dodge=False)`
    - **`Description:`** Creates a bar plot using Seaborn, where the x-axis represents 'mode' (0 = Minor, 1 = Major), the y-axis represents the average 'streams', and the bars are color-coded by 'mode' using the 'coolwarm' color palette. The `dodge=False` ensures that the bars are not separated by the hue categories.

  - **`Function:`** `plt.xlabel('Mode (0 = Minor, 1 = Major)')`
    - **`Description:`** Adds the label "Mode (0 = Minor, 1 = Major)" to the x-axis of the plot.

  - **`Function:`** `plt.ylabel('Average Streams')`
    - **`Description:`** Adds the label "Average Streams" to the y-axis of the plot.

  - **`Function:`** `plt.title('Average Streams by Mode')`
    - **`Description:`** Sets the title of the plot to "Average Streams by Mode".

  - **`Function:`** `plt.xticks([0, 1], ['Minor', 'Major'])`
    - **`Description:`** Customizes the x-axis tick labels, setting them to 'Minor' for 0 and 'Major' for 1 to represent the music modes.

  - **`Function:`** `plt.legend([], [], frameon=False)`
    - **`Description:`** Hides the legend by passing empty lists for the legend handles and labels and setting `frameon=False` to avoid displaying a legend box.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the final plot on the screen after all adjustments and customizations.

##### *Part B:*
  - **`Function:`** `Spotify_Data.groupby('artist(s)_name')[['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists', 'in_spotify_charts', 'in_apple_charts', 'in_deezer_charts', 'in_shazam_charts']].sum().reset_index()`
    - **`Description:`** Groups the `Spotify_Data` DataFrame by the 'artist(s)_name' column, then sums the appearance counts for each artist across multiple playlists and chart columns. The `reset_index()` function returns the result as a DataFrame instead of a grouped object.

  - **`Function:`** `artist_playlist_counts[['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists', 'in_spotify_charts', 'in_apple_charts', 'in_deezer_charts', 'in_shazam_charts']].sum(axis=1)`
    - **`Description:`** Sums the appearances across multiple columns (playlists and charts) for each artist and stores the result in the 'total_appearances' column.

  - **`Function:`** `artist_playlist_counts.sort_values(by='total_appearances', ascending=False).head(10)`
    - **`Description:`** Sorts the `artist_playlist_counts` DataFrame by the 'total_appearances' column in descending order and selects the top 10 artists based on total appearances.

  - **`Function:`** `plt.figure(figsize=(14, 8))`
    - **`Description:`** Creates a new figure for plotting with a specified size of 14 inches by 8 inches.

  - **`Function:`** `sns.barplot(data=top_artists, x='artist(s)_name', y='total_appearances', hue='artist(s)_name', palette='Set3', dodge=False)`
    - **`Description:`** Creates a bar plot using Seaborn, where the x-axis represents the 'artist(s)_name', the y-axis represents the 'total_appearances', and the bars are color-coded by 'artist(s)_name' using the 'Set3' color palette. `dodge=False` ensures that the bars for each artist are not separated.

  - **`Function:`** `plt.xlabel('Artist(s) Name')`
    - **`Description:`** Adds the label "Artist(s) Name" to the x-axis of the plot.

  - **`Function:`** `plt.ylabel('Total Appearances in Playlists and Charts')`
    - **`Description:`** Adds the label "Total Appearances in Playlists and Charts" to the y-axis of the plot.

  - **`Function:`** `plt.title('Top 10 Artists by Total Appearances in Playlists and Charts')`
    - **`Description:`** Sets the title of the plot to "Top 10 Artists by Total Appearances in Playlists and Charts".

  - **`Function:`** `plt.xticks(rotation=45, ha='right')`
    - **`Description:`** Rotates the x-axis labels by 45 degrees and aligns them to the right for better readability.

  - **`Function:`** `plt.show()`
    - **`Description:`** Displays the final plot after all adjustments and customizations.

  - **`Function:`** `artist_playlist_counts.set_index('artist(s)_name')[['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists', 'in_spotify_charts', 'in_apple_charts', 'in_deezer_charts', 'in_shazam_charts', 'total_appearances']]`
    - **`Description:`** Sets the 'artist(s)_name' as the index and selects the columns related to playlist and chart appearances, including the total appearances, for further analysis.

  - **`Function:`** `print(detailed_appearances.sort_values(by='total_appearances', ascending=False).head(10))`
    - **`Description:`** Displays the top 10 artists' detailed appearance counts, sorted by 'total_appearances', in a clean and readable table format.


## Code Breakdown:

##### *Part A:*
```python
# Import necessary libraries
import matplotlib.pyplot as plt
import seaborn as sns

# Group the data by 'key' and 'mode' (Major vs Minor), and calculate both the average streams and the count of tracks for each group
key_mode_streams = Spotify_Data.groupby(['key', 'mode']).agg(
    streams=('streams', 'mean'),  # Calculate the average streams per key and mode combination
    track_count=('streams', 'size')  # Count the number of tracks per key and mode combination
).reset_index()

# Display the patterns in key and mode
print("Patterns based on key and mode:")
print(key_mode_streams, "\n")

# Initialize a figure with a size of 12x6 inches for the two subplots
plt.figure(figsize=(12, 6))

# First subplot: Plot Average Streams by Key and Mode
plt.subplot(1, 2, 1)  # (1 row, 2 columns, first subplot)
sns.barplot(x='key', y='streams', hue='mode', data=key_mode_streams, palette='viridis')
plt.title('Average Streams by Key and Mode')  # Sets the title of the first subplot
plt.xlabel('Key')  # Label for x-axis
plt.ylabel('Average Streams')  # Label for y-axis

# Second subplot: Plot Track Count by Key and Mode
plt.subplot(1, 2, 2)  # (1 row, 2 columns, second subplot)
sns.barplot(x='key', y='track_count', hue='mode', data=key_mode_streams, palette='coolwarm')
plt.title('Track Count by Key and Mode')  # Sets the title of the second subplot
plt.xlabel('Key')  # Label for x-axis
plt.ylabel('Track Count')  # Label for y-axis

# Adjusts the layout to ensure subplots fit without overlap
plt.tight_layout()

# Displays the figure with the two subplots
plt.show()
```

##### *Part A.1:*
```python
# Import necessary libraries
import matplotlib.pyplot as plt
import seaborn as sns

# Patterns by Key with Multiple Colors
# Groups the data by 'key' and calculates the average streams for each musical key.
avg_streams_by_key = Spotify_Data.groupby('key')['streams'].mean()

# Resets the index to prepare the data for plotting, and converts 'key' to string for better display.
plot_data = avg_streams_by_key.reset_index()
plot_data['key'] = plot_data['key'].astype(str)  # Convert keys to strings for display

# Initializes a figure with size 10x8 inches for the bar plot.
plt.figure(figsize=(10, 8))

# Creates a bar plot using seaborn with hue applied to the 'key' column for color differentiation.
# The palette 'viridis' is applied for color grading.
sns.barplot(data=plot_data, x='key', y='streams', palette='viridis', hue='key', dodge=False)

# Labels the x-axis as 'Musical Key' to indicate the grouping variable for the bars.
plt.xlabel('Musical Key')

# Labels the y-axis as 'Average Streams' to indicate the metric being visualized.
plt.ylabel('Average Streams')

# Sets the title of the plot to 'Average Streams by Musical Key' to describe the content.
plt.title('Average Streams by Musical Key')

# Disables the legend as the 'hue' parameter is only for color and doesn't need a separate legend.
plt.legend([], [], frameon=False)

# Displays the plot.
plt.show()
```

##### *Part A.2:*
```python
# Groups the data by 'mode' (0 = Minor, 1 = Major) and calculates the average streams for each mode.
avg_streams_by_mode = Spotify_Data.groupby('mode')['streams'].mean().reset_index()

# Initializes a figure with size 10x8 inches for the bar plot.
plt.figure(figsize=(10, 8))

# Creates a bar plot to visualize the average streams for each mode (Minor vs Major).
# The 'hue' argument ensures each mode has a different color, but the legend is hidden.
sns.barplot(data=avg_streams_by_mode, x='mode', y='streams', palette='coolwarm', hue='mode', dodge=False)

# Labels the x-axis as 'Mode (0 = Minor, 1 = Major)' to distinguish between the two modes.
plt.xlabel('Mode (0 = Minor, 1 = Major)')

# Labels the y-axis as 'Average Streams' to indicate the metric being visualized.
plt.ylabel('Average Streams')

# Sets the title of the plot to 'Average Streams by Mode' to describe the content.
plt.title('Average Streams by Mode')

# Customizes the x-axis tick labels to display 'Minor' and 'Major' instead of 0 and 1.
plt.xticks([0, 1], ['Minor', 'Major'])

# Disables the legend since the 'hue' is only used for color and not for grouping data.
plt.legend([], [], frameon=False)

# Displays the plot.
plt.show()
```

##### *Part B:*
```python
# Groups the data by 'artist(s)_name' and sums the occurrences of playlist and chart appearances.
artist_playlist_counts = Spotify_Data.groupby('artist(s)_name')[[
    'in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists', 
    'in_spotify_charts', 'in_apple_charts', 'in_deezer_charts', 'in_shazam_charts'
]].sum().reset_index()

# Adds a new column 'total_appearances' by summing the playlist and chart appearances for each artist.
artist_playlist_counts['total_appearances'] = (
    artist_playlist_counts[['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists', 
                           'in_spotify_charts', 'in_apple_charts', 'in_deezer_charts', 'in_shazam_charts']].sum(axis=1)
)

# Sorts the data by 'total_appearances' in descending order and selects the top 10 artists.
top_artists = artist_playlist_counts.sort_values(by='total_appearances', ascending=False).head(10)

# Initializes a figure of size 14x8 inches for the bar plot.
plt.figure(figsize=(14, 8))

# Creates a bar plot to visualize the top 10 artists' total appearances in playlists and charts.
# The 'hue' argument ensures each artist has a different color.
sns.barplot(data=top_artists, x='artist(s)_name', y='total_appearances', hue='artist(s)_name', palette='Set3', dodge=False)

# Labels the x-axis as 'Artist(s) Name' to represent the artists.
plt.xlabel('Artist(s) Name')

# Labels the y-axis as 'Total Appearances in Playlists and Charts' for clarity.
plt.ylabel('Total Appearances in Playlists and Charts')

# Sets the title of the plot to 'Top 10 Artists by Total Appearances in Playlists and Charts'.
plt.title('Top 10 Artists by Total Appearances in Playlists and Charts')

# Rotates the x-axis labels by 45 degrees for better readability.
plt.xticks(rotation=45, ha='right')

# Displays the plot with the customizations applied.
plt.show()

# Creates a detailed table showing the number of appearances for each artist across different platforms and charts.
detailed_appearances = artist_playlist_counts.set_index('artist(s)_name')[[
    'in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists', 
    'in_spotify_charts', 'in_apple_charts', 'in_deezer_charts', 'in_shazam_charts', 'total_appearances'
]]

# Prints the detailed appearance counts of the top 10 artists, sorted by total appearances.
print("Detailed Artist Appearances in Playlists and Charts (Top 10 Artists):")
print(detailed_appearances.sort_values(by='total_appearances', ascending=False).head(10))
```

## Expected Output:

##### *Part A:*
```python
Patterns based on key and mode:
   key   mode           streams  track_count
0    A  Major  401960332.585366           42
1    A  Minor  417390630.969697           33
2   A#  Major  627533592.148148           27
3   A#  Minor       484923094.2           30
4    B  Major  436333624.942857           35
5    B  Minor   582511036.23913           46
6   C#  Major   628588294.20548           73
7   C#  Minor  566525199.276596           47
8    D  Major  572017994.909091           66
9    D  Minor  342558842.066667           15
10  D#  Major  681962300.166667           12
11  D#  Minor  479364677.285714           21
12   E  Major  760596278.764706           17
13   E  Minor  508326422.044444           45
14   F  Major       527931052.5           44
15   F  Minor  410283606.888889           45
16  F#  Major  417544999.566667           30
17  F#  Minor  595492093.883721           43
18   G  Major  492981262.454545           66
19   G  Minor       363759305.7           30
20  G#  Major  545804415.190476           63
21  G#  Minor  321903624.357143           28 
```

![image](https://github.com/user-attachments/assets/a3a1e504-143d-4c20-bc21-36bc6c2f587d)

##### *Part A.1:*

![image](https://github.com/user-attachments/assets/53086366-d4aa-4518-8dc9-a7bacecb7654)

##### *Part A.2:*

![image](https://github.com/user-attachments/assets/37e5c81e-dadb-4211-b9cc-6df4f98b83ff)

##### *Part B:*

![image](https://github.com/user-attachments/assets/5917aa4b-ec4d-4673-af40-90e17895022f)
![image](https://github.com/user-attachments/assets/95528014-f260-4824-a71b-d242bf6f5176)

---

This analysis provides comprehensive insights into the trends and characteristics of popular music tracks, helping to understand what factors contribute to higher stream counts, and how musical attributes and platforms play a role in shaping listener preferences.

### **Overall Conclusion**:
This experiment effectively demonstrates how to filter, transform, and visualize data using Python’s powerful pandas and seaborn libraries. Each problem showcases the ability to manipulate datasets to derive meaningful insights through data wrangling and visualization techniques.

---

###### Author: **Francesca Ellaiza R. Nacu**
