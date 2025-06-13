## MovieLens Data Analysis and Recommendation System

MovieLens 1M dataset

Building of a movie recommendation system using collaborative filtering. The project conducts data preprocessing, EDA, user clustering, and generates personalized movie recommendations.

## Dataset

**`ratings.dat`**
All ratings are contained in this file in the format: `UserID::MovieID::Rating::Timestamp`

* `UserID`: Ranges between 1 and 6040.
* `MovieID`: Ranges between 1 and 3952.
* `Rating`: Made on a 5-star scale (whole-star ratings only).
* `Timestamp`: Represented in seconds since the epoch.
* Each user has at least 20 ratings.

**`users.dat`**
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

**`movies.dat`**
Movie information is in this file in the format: `MovieID::Title::Genres`

* `Title`: Identical to titles from IMDB, including year of release.
* `Genres`: Pipe-separated list selected from 18 genres (Action, Adventure, Comedy, etc.)
