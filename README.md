# Movie Recommender: A Content-Based Approach

This project implements a content-based movie recommender system using Python and the scikit-learn library.

## Project Overview

The goal of this project is to build a movie recommender system that suggests movies similar to a given movie based on their content, such as cast, genre, director, and writer. The system utilizes cosine similarity to measure the similarity between movies.

## Dataset

The project uses three datasets:

* **movie_rating_df.csv:** Contains movie ratings and basic information.
* **directors_writers.csv:** Contains information about directors and writers.
* **actor_name.csv:** Contains information about actors and the movies they are known for.

These datasets are merged and preprocessed to create a feature matrix used for calculating movie similarity.

## Methodology

1. **Data Cleaning and Preprocessing:**
   * Handling missing values.
   * Cleaning and formatting data.
   * Merging datasets.

2. **Feature Engineering:**
   * Creating a feature matrix based on cast, genre, director, and writer information.
   * Sanitizing data by removing spaces and converting to lowercase.

3. **Modeling:**
   * Using CountVectorizer to create a numerical representation of the features.
   * Calculating cosine similarity between movies based on the feature matrix.

4. **Recommendation:**
   * Implementing a function that takes a movie title as input and returns a list of similar movies.
   * Sorting movies based on similarity scores and selecting the top recommendations.

## Usage

1. Clone the repository.
2. Run the notebook cells to load the data, build the model, and generate recommendations.
3. Enter a movie title to get recommendations.

## Dependencies

* Python 3.x
* pandas
* numpy
* scikit-learn
