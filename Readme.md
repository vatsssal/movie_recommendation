# Movie Recommendation System

## Overview
This project implements a **Movie Recommendation System** using **Natural Language Processing (NLP)** techniques. It suggests movies similar to a selected movie based on content-based filtering using TF-IDF vectorization and cosine similarity. The system includes:

1. **Data Preprocessing**: Extracting and cleaning movie metadata.
2. **Content-Based Recommendations**: Suggesting similar movies based on movie tags.
3. **Interactive Web Application**: A user-friendly interface powered by **Streamlit**.

---

## Features
- **Movie Similarity**: Recommends movies based on content (genres, keywords, cast, and overview).
- **Interactive UI**: Built with **Streamlit**, allowing users to search for movies and view recommendations.
- **Movie Posters**: Displays posters for recommended movies using the TMDB API.
- **Pickle Storage**: Serialized data models for efficient deployment.

---

## Table of Contents
- [Installation](#installation)
- [Dataset](#dataset)
- [Code Explanation](#code-explanation)
- [How to Run](#how-to-run)
- [Dependencies](#dependencies)
- [Future Improvements](#future-improvements)

---

## Installation
To set up and run this project locally:

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/movie-recommendation-system.git
   cd movie-recommendation-system
   ```

2. Install required Python libraries:

   ```bash
   pip install -r requirements.txt
   ```

3. Add the TMDB API key:
   - Visit [TMDB](https://www.themoviedb.org) to get your API key.
   - Replace the placeholder API key (`8265bd1679663a7ea12ac168da84d2e8`) in `app.py`.

---

## Dataset
The project uses the following datasets:
- **tmdb_5000_movies.csv**: Contains movie metadata.
- **tmdb_5000_credits.csv**: Contains movie credits (cast, crew).

Place the datasets in the `Dataset/` directory.

### Columns Used:
- `movie_id`
- `title`
- `overview`
- `genres`
- `keywords`
- `cast`
- `crew`

---

## Code Explanation

### 1. **Data Preprocessing (`ipynb` Script)**

- **Merging Datasets**: Combines `movies` and `credits` on the `title` column.
- **Cleaning Data**: Drops rows with missing values.
- **Feature Extraction**:
   - Extracts relevant fields like `genres`, `keywords`, `cast` (top 3 actors), and `crew` (director).
   - Tokenizes `overview` and combines all features into a single column called `tags`.
- **TF-IDF Vectorization**: Converts movie tags into vectors using `TfidfVectorizer` to remove stop words and limit features.
- **Cosine Similarity**: Measures similarity between movies using cosine similarity.

### 2. **Web Application (`app.py`)**

- **Model Loading**: Uses pickle files (`movie_list.pkl` and `similarity.pkl`) to load preprocessed data.
- **API Integration**: Fetches movie posters using the TMDB API.
- **Recommendation Function**: Returns 5 similar movies and their posters.
- **Streamlit UI**: Displays a dropdown for movie selection and a grid of recommendations with posters.

---

## How to Run

### Step 1: Run Data Preprocessing
Run the provided notebook to preprocess the data and generate the pickle files:

```bash
jupyter notebook
```

### Step 2: Run the Streamlit App
Start the web application by running `app.py`:

```bash
streamlit run app.py
```

### Step 3: Interact with the App
- Select a movie from the dropdown menu.
- View the top 5 recommended movies along with their posters.

---

## Dependencies
The following libraries are required:

- **Python 3.x**
- **pandas**
- **numpy**
- **scikit-learn**
- **streamlit**
- **requests**
- **pickle**

Install all dependencies using:

```bash
pip install -r requirements.txt
```

---

## Future Improvements
- **Hybrid Recommendation**: Combine content-based and collaborative filtering.
- **User Preferences**: Add features for user ratings and feedback.
- **Advanced NLP**: Use models like BERT or Sentence Transformers for better tag embeddings.
- **Deployment**: Deploy on platforms like Heroku or AWS.

---

## Acknowledgements
- [TMDB API](https://www.themoviedb.org)
- Datasets from Kaggle.

---

## License
This project is licensed under the MIT License.

---

Enjoy recommending movies! 🎬✨
