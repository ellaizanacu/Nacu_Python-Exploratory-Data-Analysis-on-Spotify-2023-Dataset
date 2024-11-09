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
- `print()` – outputs text or variable values to the console.
- `.describe()` – generates summary statistics for numerical columns, including count, mean, standard deviation, minimum, quartiles, and maximum.
- `.transpose()` – transposes the DataFrame, swapping rows and columns for easier readability.
- `f-string` – formats strings with embedded variables or expressions, used here to print a line separator.
- `.mean()` – calculates the average (mean) of a specified column.
- `.median()` – calculates the median (middle value) of a specified column.
- `.std()` – calculates the standard deviation of a specified column, showing data dispersion.

##### *Part B:*
- `plt.figure()` – initializes a new figure with a specified size for plotting.
- `sns.histplot()` – creates a histogram plot with optional KDE for visualizing the distribution of data in a specific column.
- `.title()` – adds a title to the plot.
- `.xlabel()` – labels the x-axis.
- `.ylabel()` – labels the y-axis.
- `plt.show()` – displays the plot.

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
- `.dropna()` – removes rows with missing values from the DataFrame.
- `.sort_values()` – sorts the DataFrame by a specified column.
- `.head()` – selects the top `n` rows from the DataFrame.
- `print()` – outputs text or variable values to the console.
- `plt.figure()` – initializes a new figure with a specified size for plotting.
- `sns.barplot()` – creates a bar plot, useful for comparing categorical data.
- `.title()` – adds a title to the plot.
- `.xlabel()` – labels the x-axis.
- `.ylabel()` – labels the y-axis.
- `plt.show()` – displays the plot.

##### *Part B:*
- `.value_counts()` – counts unique values in a column, useful for identifying the frequency of each artist.
- `.head()` – selects the top `n` values from the Series.
- `print()` – outputs text or variable values to the console.
- `plt.figure()` – initializes a new figure with a specified size for plotting.
- `plt.bar()` – creates a bar chart with specified labels and values.
- `plt.cm.Pastel1()` – applies a softer color palette for the bar plot.
- `.title()` – adds a title to the plot.
- `.xlabel()` – labels the x-axis.
- `.ylabel()` – labels the y-axis.
- `plt.xticks()` – adjusts x-axis label orientation for readability.
- `plt.show()` – displays the plot.

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
- `.value_counts()` – counts occurrences of each unique value in a column, useful for counting releases per year.
- `.sort_index()` – sorts the Series by its index, useful for chronological order in time series data.
- `plt.figure()` – initializes a new figure with a specified size for plotting.
- `plt.plot()` – creates a line plot with specified x and y data, markers, colors, and labels.
- `.title()` – adds a title to the plot.
- `.xlabel()` – labels the x-axis.
- `.ylabel()` – labels the y-axis.
- `.grid()` – displays a grid on the plot, with custom line style and width.
- `.legend()` – displays a legend to label different data in the plot.
- `.tight_layout()` – adjusts plot parameters for better layout.
- `plt.show()` – displays the plot.

##### *Part B:*
- `.value_counts()` – counts occurrences of each unique value in a column, useful for counting releases per month.
- `.sort_index()` – sorts the Series by its index, organizing month data chronologically.
- `plt.figure()` – initializes a new figure with a specified size for plotting.
- `.plot(kind='bar')` – creates a bar plot with specified data, labels, and colors.
- `.title()` – adds a title to the plot.
- `.xlabel()` – labels the x-axis.
- `.ylabel()` – labels the y-axis.
- `.xticks()` – customizes x-axis ticks with specified labels and rotations.
- `.grid()` – adds a grid to the plot for readability.
- `.idxmax()` – finds the index of the maximum value in the Series, indicating the peak month.
- `.max()` – finds the maximum value in the Series, representing the highest track release count.
- `.legend()` – displays a legend with the month and count of peak releases.
- `.tight_layout()` – adjusts plot parameters to prevent overlapping elements.
- `plt.show()` – displays the plot.
- `print()` – outputs text or variable values to the console.

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
##### *Part B:*

## Functions to be Used:


##### *Part A:*
##### *Part B:*


## Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

## Expected Output:

##### *Part A:*
##### *Part B:*


---

## Platform Popularity

1. **Platform Comparison**:
   - Comparison of track counts across platforms (`spotify_playlists`, `spotify_charts`, and `apple_playlists`).
   - Determination of which platform tends to favor popular tracks.

## Problem(s):
- How do the numbers of tracks in spotify_playlists, spotify_charts, and apple_playlists compare? Which platform seems to favor the most popular tracks?

## Approach:
##### *Part A:*
##### *Part B:*


## Functions to be Used:

##### *Part A:*
##### *Part B:*



## Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

## Expected Output:

##### *Part A:*
##### *Part B:*


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
##### *Part B:*


## Functions to be Used:


##### *Part A:*
##### *Part B:*



## Code Breakdown:

##### *Part A:*
```python

```

##### *Part B:*
```python

```

## Expected Output:

##### *Part A:*
##### *Part B:*


---

This analysis provides comprehensive insights into the trends and characteristics of popular music tracks, helping to understand what factors contribute to higher stream counts, and how musical attributes and platforms play a role in shaping listener preferences.

### **Overall Conclusion**:
This experiment effectively demonstrates how to filter, transform, and visualize data using Python’s powerful pandas and seaborn libraries. Each problem showcases the ability to manipulate datasets to derive meaningful insights through data wrangling and visualization techniques.

---

###### Author: **Francesca Ellaiza R. Nacu**
