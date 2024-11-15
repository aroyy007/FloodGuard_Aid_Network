# API Documentation for FloodGuard

## Overview

This API provides endpoints for managing flood victim and volunteer data, as well as storing coordinates for disaster response. It is built using **Express.js** and connected to a **MongoDB** database.

## Base URL

```
http://localhost:{port}
```

Replace `{port}` with your desired port (default is 3000).

## Endpoints

### 1. **POST /submit-victim**

-   **Description:** Submit victim data to the database.
-   **Request Body:**

    ```json
    {
        "name": "Name",
        "phone": "1234567890",
        "needs": ["Medicine", "Food"],
        "peopleCount": 2,
        "createdAt": "2024-11-15T14:30:00Z",
        "location": "123 Main St, Springfield",
        "description": "Need urgent medical help and shelter",
        "coordinates": {
            "latitude": 40.73061,
            "longitude": -73.935242
        }
        "author" : {
            "coordinates": {
                "latitude": 40.73061,
                "longitude": -73.935242
            },
            "location": "123 Main St, Springfield"
        }
    }
    ```

-   **Response:**
    ```json
    {
        "message": "Victim data stored successfully"
    }
    ```

### 2. **GET /get-victim**

-   **Description:** Retrieve all victims stored in the database.
-   **Response:**
    ```json
    {
        "data" : [
            {
                "name": "Name",
                "phone": "1234567890",
                "needs": ["Medicine", "Food"],
                "peopleCount": 2,
                "createdAt": "2024-11-15T14:30:00Z",
                "location": "123 Main St, Springfield",
                "description": "Need urgent medical help and shelter",
                "coordinates": {
                    "latitude": 40.73061,
                    "longitude": -73.935242
                }
                "author" : {
                    "coordinates": {
                        "latitude": 40.73061,
                        "longitude": -73.935242
                    },
                    "location": "123 Main St, Springfield"
                }
            },
            { ...victim data... }
        ]
    }
    ```

### 4. **POST /submit-volunteer**

-   **Description:** Submit volunteer data to the database.
-   **Request Body:**
    ```json
    {
        "author": {
            "name": "Name",
            "avatar": "https://example.com/avatar.jpg",
            "location": "123 Main St, Springfield",
        },
        "teamName": "Helping Hands",
        "memberCount": 5,
        "phoneNumber": "1234567890",
        "aidTypes": ["Medicine", "Food", "Shelter"],
        "description": "Experienced in disaster relief",
        "image": "base64-encoded-image",
        "createdAt": "2024-11-15T14:30:00Z",
        "coordinates": {
            "latitude": 40.73061,
            "longitude": -73.935242
        },
    }
    ```
-   **Response:**
    ```json
    {
      "message": "Volunteer data stored successfully",
    }
    ```

### 5. **GET /get-volunteer**

-   **Description:** Retrieve all volunteer data stored in the database.
-   **Response:**
    ```json
    {
      "data": [
        {
            "author": {
                "name": "Name",
                "avatar": "https://example.com/avatar.jpg",
                "location": "123 Main St, Springfield",
            },
            "teamName": "Helping Hands",
            "memberCount": 5,
            "phoneNumber": "1234567890",
            "aidTypes": ["Medicine", "Food", "Shelter"],
            "description": "Experienced in disaster relief",
            "image": "base64-encoded-image",
            "createdAt": "2024-11-15T14:30:00Z",
            "coordinates": {
                "latitude": 40.73061,
                "longitude": -73.935242
            },
        },
        { ...volunteer data... }
      ]
    }
    ```

## Error Handling

All error responses will return a `500` status code with a message detailing the issue:

```json
{
    "message": "Internal Server Error",
    "error": "error description"
}
```

---

## Authentication

Currently, no authentication is required for the endpoints.

---

### Conclusion

This API enables quick management of flood-related data for victims, volunteers, and disaster response teams. It provides a simple interface to help ensure efficient disaster relief.
