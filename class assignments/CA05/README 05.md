# CA05 – kNN Based Movie Recommender Engine

## Overview

This project builds a content-based movie recommendation engine using the
k-Nearest Neighbors (kNN) algorithm. Given a query movie, the engine finds
the 5 most similar movies in the dataset based on genre profile and IMDB
rating. It simulates the "More Like This" feature you'd see on a streaming
platform like Netflix or IMDb.

**Query movie:** *The Post*  
**Output:** The 5 most similar movies in the dataset

---

## Dataset

**Source:** UCI IMDB Movie Dataset (30-movie subset)  
**URL:** `https://github.com/ArinB/MSBA-CA-Data/raw/main/CA05/movies_recommendation_data.csv`

Each row represents one movie with the following columns:

| Column | Description |
|--------|-------------|
| Movie ID | Unique identifier |
| Movie Name | Title of the film |
| IMDB Rating | Numeric rating (5.9 – 8.8) |
| Biography | Genre flag (0 or 1) |
| Drama | Genre flag (0 or 1) |
| Thriller | Genre flag (0 or 1) |
| Comedy | Genre flag (0 or 1) |
| Crime | Genre flag (0 or 1) |
| Mystery | Genre flag (0 or 1) |
| History | Genre flag (0 or 1) |
| Label | All zeros — not used (no classification task) |

---

## How It Works

1. **Load** the dataset from GitHub
2. **Drop** non-feature columns (`Movie Name`, `Movie ID`, `Label`)
3. **Scale** all features using `StandardScaler` so IMDB ratings and binary genre flags are on a comparable scale
4. **Fit** a `NearestNeighbors` model with k=5 and Euclidean distance
5. **Define** the query movie "The Post" as a feature vector:
   `[IMDB=7.2, Biography=1, Drama=1, Thriller=0, Comedy=0, Crime=0, Mystery=0, History=1]`
6. **Scale** the query vector using the same scaler
7. **Query** the model and return the 5 closest movies

---

## Results

The top 5 movies recommended for *The Post*:

| Rank | Movie |
|------|-------|
| 1 | 12 Years a Slave |
| 2 | Hacksaw Ridge |
| 3 | Queen of Katwe |
| 4 | The Wind Rises |
| 5 | A Beautiful Mind |

---

## Requirements
```
pandas
scikit-learn
```

Install with:
```bash
pip install pandas scikit-learn
```

---

## Notes

- The `Label` column is all zeros and is ignored throughout; this is not a classification task.
- `StandardScaler` is applied before fitting so that the continuous IMDB rating doesn't dominate the binary genre flags in distance calculations.
- Similarity is based solely on genre flags and IMDB rating. Attributes like actors, directors, and themes are not in the dataset and are therefore not factored in.
