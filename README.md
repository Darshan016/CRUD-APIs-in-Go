# Movie CRUD API in Go

This is a simple CRUD (Create, Read, Update, Delete) API for managing movies, implemented in Go.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
  - [Create a Movie](#create-a-movie)
  - [Get All Movies](#get-all-movies)
  - [Get a Movie by ID](#get-a-movie-by-id)
  - [Update a Movie](#update-a-movie)
  - [Delete a Movie](#delete-a-movie)
- [Movie Struct](#movie-struct)
- [Contributing](#contributing)
- [License](#license)

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/Darshan016/CRUD-APIs-in-Go.git
    ```
2. Change to the project directory:
    ```sh
    cd <your_directory_name>
    ```
3. Install dependencies:
    ```sh
    go mod tidy
    ```
4. Run the application:
    ```sh
    go run main.go
    ```

## Usage

After running the application, the API will be available at `http://localhost:8080`.

## API Endpoints

### Create a Movie

- **URL:** `/movies`
- **Method:** `POST`
- **Request Body:**
    ```json
    {
        "isbn": "string",
        "title": "string",
        "director": {
            "name": "string"
        }
    }
    ```
- **Success Response:**
    - **Code:** 201 CREATED
    - **Content:**
        ```json
        {
            "id": "string",
            "isbn": "string",
            "title": "string",
            "director": {
                "name": "string"
            }
        }
        ```

### Get All Movies

- **URL:** `/movies`
- **Method:** `GET`
- **Success Response:**
    - **Code:** 200 OK
    - **Content:**
        ```json
        [
            {
                "id": "string",
                "isbn": "string",
                "title": "string",
                "director": {
                    "name": "string"
                }
            },
            ...
        ]
        ```

### Get a Movie by ID

- **URL:** `/movies/{id}`
- **Method:** `GET`
- **URL Params:**
    - **id:** `string`
- **Success Response:**
    - **Code:** 200 OK
    - **Content:**
        ```json
        {
            "id": "string",
            "isbn": "string",
            "title": "string",
            "director": {
                "name": "string"
            }
        }
        ```
- **Error Response:**
    - **Code:** 404 NOT FOUND
    - **Content:** `Movie not found`

### Update a Movie

- **URL:** `/movies/{id}`
- **Method:** `PUT`
- **URL Params:**
    - **id:** `string`
- **Request Body:**
    ```json
    {
        "isbn": "string",
        "title": "string",
        "director": {
            "name": "string"
        }
    }
    ```
- **Success Response:**
    - **Code:** 200 OK
    - **Content:**
        ```json
        {
            "id": "string",
            "isbn": "string",
            "title": "string",
            "director": {
                "name": "string"
            }
        }
        ```
- **Error Response:**
    - **Code:** 404 NOT FOUND
    - **Content:** `Movie not found`

### Delete a Movie

- **URL:** `/movies/{id}`
- **Method:** `DELETE`
- **URL Params:**
    - **id:** `string`
- **Success Response:**
    - **Code:** 204 NO CONTENT
- **Error Response:**
    - **Code:** 404 NOT FOUND
    - **Content:** `Movie not found`

## Movie Struct

```go
type Movie struct {
    ID       string    `json:"id"`
    Isbn     string    `json:"isbn"`
    Title    string    `json:"title"`
    Director *Director `json:"director"`
}

type Director struct {
    Name string `json:"name"`
}
