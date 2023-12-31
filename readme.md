# Movie API

Welcome to the Movie API! This API allows you to access and manage movie information, including movie titles, descriptions, release dates, and genres.

## What is Movie API?

The Movie API is a web-based application that serves as a backend for movie-related data. It offers a range of functionalities for managing movies and their genres through simple and secure API endpoints.

## Features

- View a list of movies with their details.
- Add new movies to the database along with their associated genres.
- Retrieve movies based on specific genres or search for movies by their titles/director/actors.
- Update movie details or genres information.
- Delete movies from the database.

## How to Use the API?

1. Make HTTP requests: You can interact with the API by sending HTTP requests using tools like `curl`, Postman, or any programming language's HTTP library.

2. Authentication: Some endpoints may require authentication for specific actions. You will need to include an API key or other authentication credentials in your request headers.

3. JSON Format: The API primarily accepts and returns data in JSON format. Ensure that your request payloads and response bodies are formatted accordingly.



## Technologies Used

- Django: A powerful web framework used for building robust and scalable web applications.
- Django REST framework: An extension of Django that simplifies building RESTful APIs.
- SQLite: The default database engine used by Django for local development, which allows you to get started quickly without setting up an external database.
- Python: The programming language used to write the backend logic and handle API requests.

## Getting Started

To get started, follow these steps:

1. Clone the project repository to your local machine, make sure to set up virtual environment.
2. Install the required dependencies using `pip install -r requirements.txt`.
3. Set up the database or use Django default database and run migrations using`python manage.py makemigrations` and  `python manage.py migrate`.
4. Start the development server using `python manage.py runserver`.

Now, you can start exploring the Movie API and managing movie data.

## Examples of Using Movie API Endpoints

### Permissions:
 when a new user registers to the system automatically a token for him is generated, in order to access some of the endpoints the user needs to have the right permission which I also add here in the endpoint examples.
Make sure to add the Token in the Request Headers with the key: Authorization and the value: Token {add here the token}.
You can get the Token from the login response or from the admin interface.

**Example Login Response:**

```json
{
    "token": string,
    "username": string
}
```

1. View the list of all movies in the database, permission: authenticated users
   
**Method:** `GET`

**Endpoint:** `/api/movies/`

2. Create a New Movie, permission: admin

**Method:** `POST`

**Endpoint:** `/api/movies/`

**Request Body example:**
```json
{
  "title": string,
  "description": string,
  "release_date": string: "yyyy-mm-dd",
  "genres": [
    {"genre": string},
    {"genre": string},
  ], 
  "director": string,
  "cast": string
}
```
3. Retrieve Movie by ID, permission: authenticated users

**Method:** `GET`

**Endpoint:** `/api/movie/{movie_id}/`

4. Update Movie details/ delete movie from database, permission: admin

**Methods:** `PUT / DELETE`

**Endpoint:** `/api/movie/{movie_id}/`

5. Search Movie by title/genre/director/actor, permission: authenticated users

**Method:** `GET`

**Endpoint:** `/api/movie/search/?title=the avengers`

**another example:**

**Endpoint:** `/api/movie/search/?genre=action`

6. View the list of all genres, permission: authenticated uses

**Method:** `GET`

**Endpoint** `/api/movie/genres/`

**Response example:**
```json 
[
    {
        "id": 1,
        "genre": "drama"
    },
    {
        "id": 2,
        "genre": "action"
    },
    {
        "id": 3,
        "genre": "crime"
    }
]
```
7. Create new genre in database, permission: admin

**Method:** `POST`

**Endpoint** `/api/movie/genres/`

**Request Body example:**
```json 

    {
        "genre": "fantasy"
    }
```
8. View genre details by name, permission: authenticated users

**Method:** `GET`

**Endpoint** `/api/movie/genres/{genre}/`

9. Change genre details by name/ delete genre from database, permission: admin

**Methods:** `PUT / DELETE`

**Endpoint** `/api/movie/genres/{genre}/`

10. Register new user to the system, permission: any

**Method:** `POST`

**Endpoint** `/api/register/`

**Request Body example**
```json
{
    "username": string,
    "password": string/int,
    "email": string,
    "first_name": string,
    "last_name": string
}
```

11. Login registered user to the system, permission: any

**Method:** `POST`

**Endpoint** `/api/login/`

**Request Body example**
```json
{
    "username": string,
    "password": string/int
}
```
## Contribution

If you find any issues or have ideas for improvements, I welcome contributions! Please feel free to open an issue or submit a pull request.

Enjoy using the Movie API!
