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

#### Problem(s):
- **Part A**: How many rows and columns does the dataset contain?
- **Part B**: What are the data types of each column?
- **Part C**: Are there any missing values?

#### Approach: 
- Load the dataset, inspect its shape and data types, check for missing values, and replace any non-numeric entries in the `streams` column.

#### Functions to be Used:
  - `pd.read_excel()` – loads the dataset from an Excel file.
  - `.shape` – returns the number of rows and columns.
  - `.dtypes` – shows data types for each column.
  - `.isnull().sum()` – counts missing values in each column.
  - `.loc[]` – accesses specific rows/columns to modify data.

#### Expected Output: 
- The shape of the dataset, data types for each column, count of missing values, and confirmation that the specified `streams` value is set to NaN.

- Overview of the dataset

![image](https://github.com/user-attachments/assets/655e3939-9391-46a3-a2d3-952aac2e947d)

- Modified data

![image](https://github.com/user-attachments/assets/2c78e27a-a85c-4dc8-bebd-6fbc96af41e4)

- *Part A*

![image](https://github.com/user-attachments/assets/39815880-9e2c-496e-8f15-02fa91add30f)

- *Part B*

![image](https://github.com/user-attachments/assets/3f948e8f-7202-4d92-a0d7-ad73f6374738)

- *Part C*

![image](https://github.com/user-attachments/assets/708e2579-0b0c-418d-8498-5618e67dc302)

--- 

## Basic Descriptive Statistics
1. **Streams Analysis**: 
   - Mean, median, and standard deviation for the `streams` column are calculated to understand central tendencies and dispersion in streaming counts.
2. **Released Year and Artist Count Distribution**: 
   - Analysis of the distribution of the `released_year` and `artist_count` columns.
   - Trends and outliers in release years and artist collaborations are identified.

#### Problem(s):
- **Part A**: What are the mean, median, and standard deviation of the streams column?
- **Part B**: What is the distribution of released_year and artist_count? Are there any noticeable trends or outliers?

#### Approach:

##### *Part A:*
Use summary statistics methods to get an overview of numerical columns and calculate specific metrics for `streams`.
- `{mean_streams}` – This represents the average number of streams across all tracks.
- `{median_streams}` – The median provides the midpoint of the streams data, less affected by outliers than the mean.
- `{std_streams}` – This measures the spread of stream counts, showing variability in track popularity.

##### *Part B:*
- Use histograms with kernel density estimates (KDE) to visualize the distribution of the release year and artist count.

#### Functions to be Used:
  - `.describe().transpose()` – displays summary statistics for numerical columns.
  - `.mean()`, `.median()`, `.std()` – calculates mean, median, and standard deviation of `streams`.
  - `sns.histplot()` – creates a histogram plot with an optional KDE line.

#### Expected Output:
- Summary statistics for all numerical columns, and the mean, median, and standard deviation for the `streams` column.

- *Part A*

![image](https://github.com/user-attachments/assets/2b139f95-7500-460a-9e09-275c1ae79a75)
![image](https://github.com/user-attachments/assets/d833ae44-701b-4eb9-96b8-00276e186ef0)

- *Part B*

  - Distribution of Released Year

![image](https://github.com/user-attachments/assets/1a8e0951-2afa-4bab-86c5-a820208d006b)

  - Distribution of Artist Count

![image](https://github.com/user-attachments/assets/9b9d685e-e8ab-4b48-877a-103390d0e1e4)


###### *Note: Only the `streams` column for "Love Grows (Where My Rosemary Goes)" is treated as `NaN`, ensuring other columns retain their original values.*

---

## Top Performers

1. **Top Streamed Tracks**:
   - The track with the highest number of streams is identified.
   - A list of the top 5 most-streamed tracks is provided for further analysis.
2. **Most Frequent Artists**:
   - The top 5 most frequent artists, based on the number of tracks in the dataset, are displayed.

#### Problem(s):
- **Part A**: Which track has the highest number of streams? Display the top 5 most streamed tracks.
- **Part B**: Who are the top 5 most frequent artists based on the number of tracks in the dataset?

#### Approach:

#### Functions to be Used:


#### Expected Output:
- Two histograms showing the distribution of the `released_year` and `artist_count`, helping to identify trends and potential outliers.


---

## Temporal Trends

1. **Tracks Released Over Time**:
   - Analysis of the number of tracks released per year. A line plot is created to show trends in annual releases.
2. **Monthly Release Patterns**:
   - Examination of release patterns by month to identify any seasonal trends.
   - Identification of the month with the highest number of track releases.

#### Problem(s):
- **Part A**: Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year.
- **Part B**: Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?

#### Approach:

#### Functions to be Used:

#### Expected Output:

---

## Genre and Music Characteristics

1. **Correlation Analysis**:
   - Examining the relationship between `streams` and attributes like `bpm`, `danceability_%`, and `energy_%`.
   - Insights into which attributes most influence track popularity.
2. **Danceability and Energy Relationship**:
   - Correlation between `danceability_%` and `energy_%` as well as between `valence_%` and `acousticness_%`.

#### Problem(s):
- **Part A**: Examine the correlation between streams and musical attributes like bpm, danceability_%, and energy_%. Which attributes seem to influence streams the most?
- **Part B**: Is there a correlation between danceability_% and energy_%? How about valence_% and acousticness_%?

#### Approach:

#### Functions to be Used:

#### Expected Output:

---

## Platform Popularity

1. **Platform Comparison**:
   - Comparison of track counts across platforms (`spotify_playlists`, `spotify_charts`, and `apple_playlists`).
   - Determination of which platform tends to favor popular tracks.

#### Problem(s):
- How do the numbers of tracks in spotify_playlists, spotify_charts, and apple_playlists compare? Which platform seems to favor the most popular tracks?

#### Approach:

#### Functions to be Used:

#### Expected Output:

---

## Advanced Analysis

1. **Key and Mode Patterns**:
   - Analysis of streaming patterns among tracks with similar `key` or `mode` (Major vs. Minor).
2. **Genres and Artists in Playlists/Charts**:
   - Identification of genres or artists that appear most frequently in playlists or charts.
   - Comparison of frequently appearing artists across platforms to determine platform-specific preferences.

#### Problem(s):
- **Part A**: Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?
- **Part B**: Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.

#### Approach:

#### Functions to be Used:

#### Expected Output:

---

This analysis provides comprehensive insights into the trends and characteristics of popular music tracks, helping to understand what factors contribute to higher stream counts, and how musical attributes and platforms play a role in shaping listener preferences.

### **Overall Conclusion**:
This experiment effectively demonstrates how to filter, transform, and visualize data using Python’s powerful pandas and seaborn libraries. Each problem showcases the ability to manipulate datasets to derive meaningful insights through data wrangling and visualization techniques.

---

###### Author: **Francesca Ellaiza R. Nacu**
