# Hybrid Movie Recommender with a Streamlit Dashboard

An interactive movie recommender built on the **MovieLens 32M** dataset (32M ratings, 2M tags, 87,585 movies). It blends collaborative filtering, content-based modeling, and a popularity prior, then re-ranks results for diversity.

*Texas A&M University, DAEN 400, Case Study 3, Fall 2025. Individual project.*

## How It Works
A user rates 5 random movies on a 0 to 5 slider. They can swap out movies they haven't seen or shuffle all 5. They then get **10 personalized recommendations** with posters.

| Component | Method |
|---|---|
| Content model | TF-IDF features from genres and tags; the user profile is the average vector of rated movies |
| Collaborative filtering | LensKit **item-item KNN** |
| Popularity prior | Average rating × log(number of ratings + 1), so well-rated, widely-rated films rank higher without dominating |
| Hybrid blend | Min-max normalized scores combined with **user-adjustable weights** |
| Diversity | **Maximal Marginal Relevance (MMR)** re-ranking to avoid near-duplicate picks |
| UI | **Streamlit** sidebar weight sliders ("personality" vs. "mainstream"), a weight-contribution chart, a popular-vs-niche toggle, TMDB API posters, caching, and session state |

## Comparison to Industry Systems
The design is a simplified version of the hybrid approaches used by Netflix and Spotify, which combine content signals with collaborative filtering. The report discusses what those systems add, such as viewing time, language, and trend signals.

## Limitations & Next Steps
- Relies on simple genre and tag metadata, and leans somewhat mainstream.
- The same blend weights are used for every user.
- Next steps: user accounts with saved ratings, an "already watched" filter, demographic personalization, and public deployment.

## Tech Stack
Python, LensKit, Streamlit, pandas, scikit-learn (TF-IDF), TMDB API

## Repository Contents
- `reports/Movie_Recommender_Report.pdf`: technical report with dashboard screenshots
- `reports/Movie_Recommender_Presentation.pdf`: slide deck

> Source code (`model2.py`, `app.py`) will be added. To run it you need the [MovieLens 32M dataset](https://grouplens.org/datasets/movielens/) and a TMDB API key.
