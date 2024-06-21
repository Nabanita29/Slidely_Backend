# Backend Server for Submission Handling

Greetings ! I am Nabanita Chatterjee and this project is a simple backend server built with Express and TypeScript. It provides APIs to save and retrieve form submissions, storing data in a JSON file.

## Prerequisites

- Node.js (v12 or later)
- npm (Node package manager)

## Setup Instructions

1. Clone the repository:
    ```sh
    git clone https://github.com/Nabanita29/Slidely_Backend
    cd Slidely_Backend
    ```

2. Install dependencies:
    ```sh
    npm install
    ```

3. Create a `db.json` file in the root directory of the project. The initial content of the file should be an empty array:
    ```json
    []
    ```

4. Compile the TypeScript files:
    ```sh
    npm run build
    ```

5. Start the server:
    ```sh
    npm start
    ```

## API Endpoints

### 1. Ping Endpoint
- **URL:** `/ping`
- **Method:** GET
- **Description:** A simple endpoint to check if the server is running. It always returns `true`.

#### Request
- **Headers:** None
- **Body:** None

#### Response
- **Status Code:** 200
- **Body:**
    ```json
    true
    ```

### 2. Submit Endpoint
- **URL:** `/submit`
- **Method:** POST
- **Description:** Saves a form submission to the JSON file.

#### Request
- **Headers:** `Content-Type: application/json`
- **Body:**
    ```json
    {
        "name": "John Doe",
        "email": "john.doe@example.com",
        "phone": "123-456-7890",
        "github_link": "https://github.com/johndoe",
        "stopwatch_time": "00:01:23"
    }
    ```

#### Response
- **Status Code:** 201
- **Body:**
    ```json
    {
        "message": "Submission saved successfully."
    }
    ```

### 3. Read Endpoint
- **URL:** `/read`
- **Method:** GET
- **Description:** Retrieves a specific form submission based on the provided index.

#### Request
- **Query Parameters:**
    - `index` (integer) - The zero-based index of the submission to retrieve.

#### Response
- **Status Code:** 200
- **Body:** (Example)
    ```json
    {
        "name": "John Doe",
        "email": "john.doe@example.com",
        "phone": "123-456-7890",
        "github_link": "https://github.com/johndoe",
        "stopwatch_time": "00:01:23"
    }
    ```
- **Status Code:** 404 (if the index is out of range)
- **Body:**
    ```json
    {
        "message": "Submission not found."
    }
    ```

## JSON Database Structure

The `db.json` file stores submissions as an array of objects. Each object represents a form submission:
```json
[
    {
        "name": "John Doe",
        "email": "john.doe@example.com",
        "phone": "123-456-7890",
        "github_link": "https://github.com/johndoe",
        "stopwatch_time": "00:01:23"
    }
    // More submissions...
]
