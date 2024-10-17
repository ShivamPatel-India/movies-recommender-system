# Movie Recommender System
<img width="770" alt="image" src="https://github.com/user-attachments/assets/0638831f-489a-4601-ad4c-25bed93365d5">

This project is a **content-based movie recommender system** that suggests movies similar to a given movie. It uses data from **TMDB (The Movie Database)**, including genres, keywords, cast, and crew, to create a recommendation model based on movie similarity. The system leverages **cosine similarity** between movie descriptions (tags) to make suggestions.

The project is live at: [Movie Recommender System on Render](https://movies-recommender-system-ymgc.onrender.com/)

## Features
- **Movie recommendations** based on content similarity.
- Fetches and displays **movie posters** from TMDB.
- Provides the top 5 recommended movies for any movie selected by the user.

## Dataset
This project uses the **TMDB 5000 Movies** and **TMDB 5000 Credits** datasets, which contain information about movie genres, keywords, cast, crew, and overview.

You can access the dataset here: [TMDB Movie Metadata on Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata/data)

## How It Works
1. **Data Preprocessing**:
   - The data from `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` is merged based on the movie title.
   - We extract and clean relevant information like `genres`, `keywords`, `cast`, and `crew`.
   - A combined "tags" column is created for each movie, containing relevant features.
   
2. **Text Vectorization and Similarity**:
   - The `tags` column is vectorized using `CountVectorizer` to create a matrix of token counts.
   - **Cosine similarity** is calculated between movies based on their vector representations.
   
3. **Movie Recommendations**:
   - For a selected movie, the app calculates the cosine similarity with all other movies and suggests the top 5 most similar movies.
   
4. **Poster Fetching**:
   - The app uses the TMDB API to fetch movie posters and display them along with the recommended titles.

## Project Structure

- **app.py**: The main Streamlit app that handles user input, shows recommendations, and fetches movie posters.
- **movie_recommender_system.py**: The backend code for preprocessing the data, calculating cosine similarity, and recommending movies.
- **model/ directory**: Stores preprocessed data files (`movies_list.pkl`, `similarity.pkl`) for faster loading.

## Requirements

Make sure you have the following libraries installed:

```bash
streamlit
numpy
pandas
scikit-learn
requests
nltk
python-dotenv
```

You can install them using:

```bash
pip install -r requirements.txt
```

## Running Locally

To run the app locally, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/ShivamPatel-India/movies-recommender-system.git
   cd movies-recommender-system
   ```

2. Install the required libraries:

   ```bash
   pip install -r requirements.txt
   ```

3. Set up your **TMDB API Key**:

   Create a `.env` file in the root of the project and add your API key:

   ```
   TMDB_API_KEY=your_api_key_here
   ```

4. Run the Streamlit app:

   ```bash
   streamlit run app.py
   ```

5. Open your browser and go to `http://localhost:8501` to view the app.

## Usage

- **Select a Movie**: Use the dropdown to select a movie.
- **Show Recommendations**: Click the "Show Recommendation" button to display the top 5 recommended movies along with their posters.

