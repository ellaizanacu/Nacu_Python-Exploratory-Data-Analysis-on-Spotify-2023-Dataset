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
![image](https://github.com/user-attachments/assets/655e3939-9391-46a3-a2d3-952aac2e947d)
![image](https://github.com/user-attachments/assets/2c78e27a-a85c-4dc8-bebd-6fbc96af41e4)

--- 

## Basic Descriptive Statistics
1. **Streams Analysis**: 
   - Mean, median, and standard deviation for the `streams` column are calculated to understand central tendencies and dispersion in streaming counts.
   
2. **Released Year and Artist Count Distribution**: 
   - Analysis of the distribution of the `released_year` and `artist_count` columns.
   - Trends and outliers in release years and artist collaborations are identified.

---

## Top Performers

1. **Top Streamed Tracks**:
   - The track with the highest number of streams is identified.
   - A list of the top 5 most-streamed tracks is provided for further analysis.
   
2. **Most Frequent Artists**:
   - The top 5 most frequent artists, based on the number of tracks in the dataset, are displayed.

---

## Temporal Trends

1. **Tracks Released Over Time**:
   - Analysis of the number of tracks released per year. A line plot is created to show trends in annual releases.
   
2. **Monthly Release Patterns**:
   - Examination of release patterns by month to identify any seasonal trends.
   - Identification of the month with the highest number of track releases.

---

## Genre and Music Characteristics

1. **Correlation Analysis**:
   - Examining the relationship between `streams` and attributes like `bpm`, `danceability_%`, and `energy_%`.
   - Insights into which attributes most influence track popularity.
   
2. **Danceability and Energy Relationship**:
   - Correlation between `danceability_%` and `energy_%` as well as between `valence_%` and `acousticness_%`.

---

## Platform Popularity

1. **Platform Comparison**:
   - Comparison of track counts across platforms (`spotify_playlists`, `spotify_charts`, and `apple_playlists`).
   - Determination of which platform tends to favor popular tracks.

---

## Advanced Analysis

1. **Key and Mode Patterns**:
   - Analysis of streaming patterns among tracks with similar `key` or `mode` (Major vs. Minor).
   
2. **Genres and Artists in Playlists/Charts**:
   - Identification of genres or artists that appear most frequently in playlists or charts.
   - Comparison of frequently appearing artists across platforms to determine platform-specific preferences.

---

This analysis provides comprehensive insights into the trends and characteristics of popular music tracks, helping to understand what factors contribute to higher stream counts, and how musical attributes and platforms play a role in shaping listener preferences.

