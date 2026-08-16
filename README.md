# Movie Recommendation System

This project is a lightweight movie recommendation system built with Python, semantic search, and vector embeddings. It uses the MovieLens dataset and a sentence-transformers model to convert movie titles and genres into vector representations, which are then stored in a ChromaDB collection for similarity-based recommendations.

## Features

- Loads the movie dataset from a CSV file
- Combines title and genres into searchable text
- Encodes movie descriptions into embeddings using SentenceTransformers
- Stores embeddings in ChromaDB
- Accepts a user preference prompt and retrieves the most relevant movie matches
- Performs semantic search instead of exact keyword matching

## Tech Stack

- Python
- pandas
- sentence-transformers
- ChromaDB
- gdown
- Jupyter Notebook

## Project Structure

- `movie_recomm_sys_using_semantic_search.ipynb` — main notebook containing the full workflow

## Setup

1. Clone the repository.
2. Create and activate a virtual environment:

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

3. Install the required libraries:

   ```bash
   pip install pandas gdown chromadb sentence-transformers
   ```

4. Open the notebook and run the cells sequentially.

## How it Works

1. The dataset is loaded from `movies.csv`.
2. A text feature is created from each movie's title and genres.
3. The `all-MiniLM-L6-v2` sentence-transformer model converts each movie feature into embeddings.
4. The embeddings are inserted into a ChromaDB collection.
5. The user enters a description such as "movies like action and adventure".
6. The system queries the vector database and returns the closest movie matches.

## Example

```python
user_feature = input("What kind of genres of movies do you like?")
recommendations = collection.query(query_texts=[user_feature], n_results=3)
print(recommendations)
```

## Notes

- The project uses a downloaded dataset file that may need to be available locally when running the notebook.
- If the dataset is missing, the notebook may need to fetch it before the embeddings step.
- For large-scale usage, you may want to persist the ChromaDB collection to disk instead of creating it in memory.

## License

This project is for educational and personal use.
