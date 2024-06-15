import requests

# Function to fetch movie details
def get_movie_info(title):
    base_url = "http://www.omdbapi.com/"
    api_key = "your_api_key_here"  # Replace with your actual OMDB API key
    params = {
        "apikey": api_key,
        "t": title,
        "plot": "full"  # or "short" for shorter plot summary
    }
    
    try:
        response = requests.get(base_url, params=params)
        data = response.json()
        if data["Response"] == "True":
            print(f"Title: {data['Title']}")
            print(f"Released: {data['Released']}")
            print(f"Plot: {data['Plot']}")
            print(f"Director: {data['Director']}")
            print(f"Actors: {data['Actors']}")
            print(f"IMDB Rating: {data['imdbRating']}")
        else:
            print("Movie not found!")
    except requests.exceptions.RequestException as e:
        print(f"Error fetching data: {e}")

# Example usage
if __name__ == "__main__":
    movie_title = "Crimson Peak"
    get_movie_info(movie_title)
