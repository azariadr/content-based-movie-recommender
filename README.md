# Movie Recommender: A Content-Based Approach

This repository contains a Content-Based Movie Recommender System built using real-time dataset streaming from IMDb's public datasets. The system suggests movies based on shared metadata such as genres, cast, directors, and writers using TF-IDF representation (via CountVectorizer) and Cosine Similarity metrics.

## Project Overview

Finding the perfect movie to watch can be overwhelming. This project aims to solve that by recommending the top 10 movies most similar to a user's favorite film. It processes, cleans, and merges multiple IMDb datasets in memory using chunked reading to balance speed and accuracy.

### Key Features
- **In-Memory Filtering:** Dynamically streams and filters modern movies (released between 2000 and 2026) directly from live IMDb datasets.
- **Data Imputation & Cleaning:** Implements K-Nearest Neighbors (`KNNImputer`) to fill missing runtime values and standardizes textual formats.
- **Metadata Soup Generation:** Merges key content predictors (Top 3 cast members, genres, directors, and writers) into a single vectorized representation.
- **Similarity Computation:** Utilizes `Cosine Similarity` to compute pairwise metadata matching scores.


## Tech Stack

- **Programming Language:** Python 3
- **Libraries:**
  - **Data Processing:** `pandas`, `numpy`
  - **Machine Learning & NLP:** `scikit-learn` (`CountVectorizer`, `KNNImputer`, `cosine_similarity`)
  - **Data Sources:** Live IMDb TSV Datasets (`title.basics`, `title.ratings`, `title.crew`, `name.basics`)
 

## How It Works

1. **Data Gathering & Ingestion:** 
   The dataset is dynamically streamed using `pandas.read_csv` in chunks to optimize memory overhead. We filter for only modern feature films (2000–2026).
2. **Feature Engineering (The "Soup"):** 
   We extract and clean multiple columns to build a rich metadata block for each movie:
   $$\text{Soup} = \text{Cast (Top 3)} + \text{Genres} + \text{Directors} + \text{Writers}$$
3. **Vectorization & Similarity Metric:** 
   The textual soup is converted into token counts using `CountVectorizer`. The cosine similarity is calculated between all vector pairs:
   $$\text{Similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|}$$
4. **Recommendation Retrieval:** 
   When a user inputs a movie title, the system returns the 10 movies with the highest similarity scores.

## Installation & Usage

### Prerequisites
Make sure you have Python installed, then install the dependencies:
```bash
pip install pandas numpy scikit-learn
```

### Running the Recommender
1. Open and run all cells in the Jupyter/Colab notebook.
2. When prompted, input any movie present in the database (e.g., `Avatar`):
```python
Enter the movie title: Avatar
```
3. The model will instantly generate a structured table listing the top 10 most similar movie recommendations.
