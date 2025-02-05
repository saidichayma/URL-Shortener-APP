# URL-Shortener-APP

## Description
This is a simplified version of a URL shortening service. This service allows users to input a long URL and receive a shortened version, similar to what Bit.ly does.
The shortened URL should redirect to the original URL when accessed.

## Documentation

The application has 2 API endpoints:

### 1. `POST /shorten`
**Description:** Creates a short URL.
- **Input:** Accepts a long URL.
- **Output:** Returns a shortened URL.
- **Method:** `POST`
- **Content-Type:** `application/json`

**Example:**
```http
POST http://localhost:8081/shorten
Content-Type: application/json

{
  "longUrl": "https://www.test.com"
}
```

---

### 2. `GET /{id}`
**Description:** Retrieves the short URL and redirects to the original URL.
- **Input:** Accepts an ID of the shortened URL.
- **Output:** Redirects to the original URL.
- **Method:** `GET`

**Example:**
```http
GET http://localhost:8081/{id}  # Redirects to the original URL.
```

## Installation & Configuration

To run the application, you need to install and run `npm` on both the **main service** and the **frontend service**.

### Steps:

1. Clone the repository:
   ```sh
   git clone <repository_url>
   ```
2. Navigate to the **frontend** folder:
   ```sh
   cd URL-shortening-frontend-main
   ```
3. Create a `.env` file with the following content:
   ```ini
   REACT_APP_API_BASE_URL=http://localhost:8081
   ```
4. Run the following commands:
   ```sh
   npm install
   npm run
   ```
5. Navigate to the **backend** folder:
   ```sh
   cd URL-shortening-service-main
   ```
6. Create a `.env` file with the following content:
   ```ini
   SERVER_PORT=8081
   MONGODB_URI=mongodb+srv://your_username:your_password@cluster0.dxcfz.mongodb.net/urlDB?retryWrites=true&w=majority&appName=Cluster0
   BASE_URL=http://localhost:8081
   ```
7. Run the following commands:
   ```sh
   npm install
   npm run
   ```
8. The app is ready! You can start testing it at:
   ```
   http://localhost:3000/

## Tests

The backend service includes three test files to validate the core functionalities of the application. You can run them using the following command:

1. Navigate to the **backend** folder:
   ```sh
   cd URL-shortening-service-main
   ```
2. Run the tests:
   ```sh
   npm test
   ```

### API Tests (`test.api.js`)
These tests check the API endpoints:
- **Get Short URL:** Ensures that a shortened URL redirects correctly (expects HTTP 302).
- **Invalid Short URL:** Ensures that a non-existing short URL returns a 404 error.
- **Invalid URL:** Ensures that an improperly formatted URL is rejected (expects HTTP 400).
- **Create URL:** Tests if a valid URL can be shortened successfully (expects HTTP 201).
- **URL Already Exists:** Ensures duplicate URLs return a status code of 208.

### Database Connection Test (`mongo.test.js`)
This test ensures that the application can connect to MongoDB successfully.
- **MongoDB Connection:** Checks if the database connection is established (expects a valid state).

### Service Logic Tests (`service.test.js`)
These tests validate internal functions:
- **isUrl:** Checks if the function correctly identifies valid URLs.
- **isNotUrl:** Ensures invalid URLs are detected properly.
- **Generate Id:** Validates that the generated IDs have the correct length (expects 6 characters).
