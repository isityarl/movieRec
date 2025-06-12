# MovieLens Data Analysis and Recommendation System

MovieLens 1M dataset, which contains 1,000,209 anonymous ratings of approximately 3,900 movies from 6,040 MovieLens users who joined in 2000.

Building of a movie recommendation system using collaborative filtering and user segmentation techniques. The project conducts data preprocessing, exploratory data analysis (EDA), user clustering, and finally, generates personalized movie recommendations.

## Dataset Description

### `ratings.dat`
All ratings are contained in this file in the format: `UserID::MovieID::Rating::Timestamp`

* `UserID`: Ranges between 1 and 6040.
* `MovieID`: Ranges between 1 and 3952.
* `Rating`: Made on a 5-star scale (whole-star ratings only).
* `Timestamp`: Represented in seconds since the epoch.
* Each user has at least 20 ratings.

### `users.dat`
User information is in this file in the format: `UserID::Gender::Age::Occupation::Zip-code`

* `Gender`: `"M"` for male and `"F"` for female.
* `Age`: Chosen from the following ranges:
  * 1: "Under 18"
  * 18: "18-24"
  * 25: "25-34"
  * 35: "35-44"
  * 45: "45-49"
  * 50: "50-55"
  * 56: "56+"
* `Occupation`: Chosen from a list of 21 choices (e.g., "academic/educator", "programmer", "student", etc.).

### `movies.dat`
Movie information is in this file in the format: `MovieID::Title::Genres`

* `Title`: Identical to titles from IMDB, including year of release.
* `Genres`: Pipe-separated list selected from 18 genres (Action, Adventure, Comedy, etc.).

## Features & Analysis

### 1. Data Loading and Preprocessing
* **Datasets**: Loads the `movies.dat`, `users.dat`, and `ratings.dat` files.
* **Data Cleaning**:
  * Assigns appropriate headers to the columns.
  * Converts Unix timestamps into a readable `YYYY-MM-DD HH:MM:SS` format.
  * Merges user data with an external zip code file (`uszips.csv`) to get geographical information.
  * Checks for and reports null values and duplicate rows.

### 2. Exploratory Data Analysis (EDA)
* **User Geolocation**: Plots the geographical distribution of users across the United States.
* **Weighted Movie Ratings**: Calculates a weighted rating for each movie to provide a more accurate ranking system that balances average rating with the number of ratings.
* **Genre Analysis**: Determines the most popular genres and analyzes the relationship between genre popularity and average rating.

### 3. User Segmentation with K-Means Clustering
* **User-Genre Preferences**: Creates a user-preference matrix based on users' average ratings for genres.
* **Finding Optimal Clusters**: Uses the **Elbow Method** and the **Silhouette Score** to determine the optimal number of user clusters.
* **Clustering and Visualization**: Applies K-Means clustering to group users into segments and uses PCA to visualize the clusters.

### 4. Movie Recommendation Engines
* **Popularity-Based (By City)**: A simple model that recommends the top 10 most-rated movies for a given city.
* **Collaborative Filtering (User-User)**:
  * Calculates **cosine similarity** between users based on their rating profiles.
  * For a target user, it identifies the most similar users and recommends movies they rated highly.
  * Recommendations are ranked by a weighted score (`Weight = Rating * Similarity`) to prioritize movies liked by the most similar users.

