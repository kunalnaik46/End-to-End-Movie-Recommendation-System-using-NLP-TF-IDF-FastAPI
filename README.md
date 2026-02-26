# 🎬 Hybrid Movie Recommendation System

A production-style Hybrid Movie Recommendation System built using:

- ⚡ FastAPI (Backend API)
- 🎨 Streamlit (Frontend UI)
- 🧠 TF-IDF + Cosine Similarity (Content-Based Filtering)
- 🌍 TMDB API (Live Movie Metadata & Posters)

This system combines local ML-based similarity with real-time TMDB data to provide rich, Netflix-style recommendations.

---

# 🚀 Features

## 🔎 Smart Search
- Keyword-based movie search
- Autocomplete suggestions
- Live TMDB search integration

## 📄 Movie Details Page
- Poster
- Backdrop image
- Overview
- Release date
- Genres
- Rating

## 🤖 Hybrid Recommendation Engine

### 1️⃣ TF-IDF Content-Based Recommendations
- Built using movie metadata
- Cosine similarity on TF-IDF matrix
- Returns top similar movies

### 2️⃣ Genre-Based Recommendations
- Uses TMDB Discover API
- Suggests popular movies from same genre

## 🏠 Dynamic Home Feed
- Trending
- Popular
- Top Rated
- Now Playing
- Upcoming

---

# 🏗 System Architecture


Streamlit (Frontend UI)
↓
FastAPI (Backend API)
↓
Hybrid Recommendation Engine
├── TF-IDF Similarity (Local Model)
└── TMDB API (Live Metadata)


---

# 📁 Project Structure


End to end movie recommendation system/
│
├── main.py # FastAPI backend
├── app.py # Streamlit frontend
├── df.pkl # Processed movie dataframe
├── indices.pkl # Title-to-index mapping
├── tfidf_matrix.pkl # TF-IDF sparse matrix
├── movies_metadata.csv
├── tmdb_500_movies.csv
├── tmdb_500_credits.csv
├── requirements.txt
└── README.md


---

# 🧠 Recommendation Logic

## Content-Based Filtering (TF-IDF)

1. Combine movie features (overview, genres, etc.)
2. Apply TF-IDF vectorization
3. Compute cosine similarity:

```python
similarity_scores = tfidf_matrix @ query_vector.T

Return top N most similar movies

Genre-Based Filtering

Fetch selected movie from TMDB

Extract primary genre

Call TMDB /discover/movie

Return popular movies from same genre

🔑 Environment Setup
1️⃣ Install Python

Recommended: Python 3.10+

Make sure Python is added to PATH.

2️⃣ Install Dependencies
Option A — Using requirements.txt
pip install -r requirements.txt
Option B — Manual Install
pip install fastapi uvicorn streamlit pandas numpy scikit-learn scipy httpx python-dotenv requests
3️⃣ Add TMDB API Key

Create a .env file in project root:

TMDB_API_KEY=your_tmdb_api_key_here

Get API key from:
https://www.themoviedb.org/settings/api

▶️ Running the Application
Start Backend (FastAPI)
python -m uvicorn main:app

Backend runs at:

http://127.0.0.1:8000

Test health endpoint:

http://127.0.0.1:8000/health
Start Frontend (Streamlit)
python -m streamlit run app.py --server.fileWatcherType none

Frontend runs at:

http://localhost:8501
