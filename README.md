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
2. Navigate to the **backend** folder:
   ```sh
   cd URL-shortening-service-main
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
5. Navigate to the **frontend** folder:
   ```sh
   cd URL-shortening-frontend-main
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
   http://localhost:8081/
