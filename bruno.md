# Bruno API Testing Guide

This document lists all the available endpoints for the **Hono API with Auth Crash Course** and how to configure them in [Bruno](https://www.usebruno.com/) (or any other API client like Postman/Insomnia).

Base URL: `http://localhost:3000`

---

## 1. Authentication (`/auth`)

These endpoints are public and do not require any headers.

### Register a new user
- **Method**: `POST`
- **URL**: `http://localhost:3000/auth/register`
- **Body** (JSON):
  ```json
  {
    "email": "user@example.com",
    "password": "strongpassword123"
  }
  ```

### Login
- **Method**: `POST`
- **URL**: `http://localhost:3000/auth/login`
- **Body** (JSON):
  ```json
  {
    "email": "user@example.com",
    "password": "strongpassword123"
  }
  ```
> **Note:** This will return a JSON response containing a JWT token (e.g., `{ "token": "ey..." }`). You will need this token for the next section.

---

## 2. Managing API Keys (`/api-keys`)

These endpoints require the JWT token you received from logging in. 
In Bruno, go to the **Headers** tab or the **Auth** -> **Bearer Token** tab and add:
- `Authorization: Bearer <your_jwt_token>`

### Get all your API Keys
- **Method**: `GET`
- **URL**: `http://localhost:3000/api-keys`

### Create a new API Key
- **Method**: `POST`
- **URL**: `http://localhost:3000/api-keys`
- **Body** (JSON):
  ```json
  {
    "name": "My Testing Key"
  }
  ```
> **Important:** This will return your raw API Key (e.g., `{ "key": "...", "id": "..." }`). Save this key! You will need it to modify Authors and Books. It is only shown once.

### Delete an API Key
- **Method**: `DELETE`
- **URL**: `http://localhost:3000/api-keys/:id`
*(Replace `:id` with the API Key ID)*

---

## 3. Authors (`/authors`)

### Get all Authors (Public)
- **Method**: `GET`
- **URL**: `http://localhost:3000/authors`

### Get a specific Author (Public)
- **Method**: `GET`
- **URL**: `http://localhost:3000/authors/:id`

### Create/Update/Delete Authors (Protected)
These endpoints require your generated **API Key** (not the JWT token).
In Bruno, go to the **Headers** tab and add:
- `X-API-Key: <your_api_key>`

#### Create an Author
- **Method**: `POST`
- **URL**: `http://localhost:3000/authors`
- **Body** (JSON):
  ```json
  {
    "name": "J.K. Rowling",
    "birthday": "1965-07-31"
  }
  ```

#### Update an Author
- **Method**: `PUT`
- **URL**: `http://localhost:3000/authors/:id`
- **Body** (JSON) - *fields are optional*:
  ```json
  {
    "name": "Joanne Rowling"
  }
  ```

#### Delete an Author
- **Method**: `DELETE`
- **URL**: `http://localhost:3000/authors/:id`

---

## 4. Books (`/books`)

### Get all Books (Public)
- **Method**: `GET`
- **URL**: `http://localhost:3000/books`

### Get a specific Book (Public)
- **Method**: `GET`
- **URL**: `http://localhost:3000/books/:id`

### Create/Update/Delete Books (Protected)
Like Authors, these endpoints require the `X-API-Key: <your_api_key>` header.

#### Create a Book
- **Method**: `POST`
- **URL**: `http://localhost:3000/books`
- **Body** (JSON):
  ```json
  {
    "title": "Harry Potter and the Sorcerer's Stone",
    "description": "A boy finds out he's a wizard.",
    "publishDate": "1997-06-26",
    "pageCount": 223,
    "authorId": "AUTHOR_UUID_HERE" 
  }
  ```
*(Replace `AUTHOR_UUID_HERE` with an actual Author ID from the `GET /authors` endpoint)*

#### Update a Book
- **Method**: `PUT`
- **URL**: `http://localhost:3000/books/:id`
- **Body** (JSON) - *fields are optional*:
  ```json
  {
    "pageCount": 309
  }
  ```

#### Delete a Book
- **Method**: `DELETE`
- **URL**: `http://localhost:3000/books/:id`
