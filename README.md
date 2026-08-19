# Movie Recommendation System

A content-based movie recommendation application built with **Python, Pandas and Streamlit**. The application uses a precomputed movie-similarity matrix to recommend movies related to a user's selected title and optionally enriches recommendations with metadata from the OMDb API.

## Overview

```text
Select a Movie
      ↓
Movie Dataset
      ↓
Similarity Matrix
      ↓
Top 5 Similar Movies
      ↓
Optional OMDb Metadata
      ↓
Streamlit Results UI
```

The current application loads `movie_dict.pkl` and `similarity.pkl`, finds the selected movie in the movie table, ranks similarity scores, and returns the five highest-scoring alternatives. fileciteturn8file0

## Features

- Select a movie from the available dataset.
- Generate five similar movie recommendations.
- Display poster, plot, genre, cast, director, language, year and rating when OMDb metadata is available.
- Stream recommendations through a simple Streamlit interface.
- Run without an OMDb key when only recommendation titles are required; metadata enrichment is optional.

## Tech Stack

- Python
- Pandas
- Streamlit
- Requests
- Pickle-based precomputed similarity data
- OMDb API for optional metadata enrichment

## Project Structure

```text
.
├── app.py
├── movie_dict.pkl
├── similarity.pkl
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/Jaswanth170/Movie-Recommendation-System.git
cd Movie-Recommendation-System
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

macOS / Linux:

```bash
source .venv/bin/activate
```

Windows:

```powershell
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Optional: configure OMDb

The application reads the API key from the `OMDB_API_KEY` environment variable. **Do not put a real API key in the source code.**

Copy `.env.example` as a reference and configure the variable in your local environment or Streamlit deployment secrets.

Example:

```bash
export OMDB_API_KEY="your_key_here"
```

On Windows PowerShell:

```powershell
$env:OMDB_API_KEY="your_key_here"
```

### 5. Run the application

```bash
streamlit run app.py
```

## Recommendation Logic

The recommendation engine uses the selected movie's row in a precomputed similarity matrix. It ranks all candidate movies by similarity score and returns the top five matches, excluding the selected movie itself. fileciteturn8file0

This repository currently stores the generated recommendation artifacts (`movie_dict.pkl` and `similarity.pkl`) rather than documenting the original dataset preprocessing pipeline. Therefore, no unsupported claim is made about the exact feature-engineering method used to create the similarity matrix.

## Security

The application previously contained an API key directly in `app.py`. The code has been updated to read `OMDB_API_KEY` from the environment instead. Keep real credentials out of Git history and source files.

## Limitations

- Recommendation quality depends on the precomputed similarity matrix.
- The original feature-engineering/training pipeline is not currently included in the repository.
- OMDb metadata requires a valid API key and network access.
- No formal offline recommendation-quality benchmark is currently documented.

## Future Improvements

- Rebuild and document the complete preprocessing pipeline.
- Replace serialized artifacts with a reproducible recommendation-generation script.
- Add recommendation evaluation metrics.
- Add caching for OMDb requests.
- Add error handling and retry policies for external API failures.
- Add automated tests.
- Deploy the Streamlit application.

## Author

**Jaswanth ST**  
GitHub: [@Jaswanth170](https://github.com/Jaswanth170)
