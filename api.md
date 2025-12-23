# Project Atlas – API Documentation

Project Atlas is a REST-based backend service used for managing users
and orders. This document describes authentication, API endpoints,
and error handling.

---

## Authentication

Project Atlas uses token-based authentication.

Authentication flow:
1. Users log in using their username and password.
2. The system generates an access token.
3. The token must be included in every protected API request.

Authorization header format:
Authorization: Bearer <access_token>

Token rules:
- Tokens are valid for 24 hours.
- Expired tokens must be regenerated.
- Missing or invalid tokens result in HTTP 401 Unauthorized.

---

## Base URL

https://api.project-atlas.com

---

## API Endpoints

### 1. GET /users

Description:
Returns a list of all users.

Authentication:
Not required.

Response:
- 200 OK

---

### 2. POST /users

Description:
Creates a new user.

Authentication:
Required.

Request body:
- name (string)
- email (string)

Response:
- 201 Created
- 400 Bad Request (invalid input)
- 401 Unauthorized

---

### 3. GET /users/{id}

Description:
Fetches details of a specific user by ID.

Authentication:
Required.

Response:
- 200 OK
- 401 Unauthorized
- 404 Not Found

---

### 4. POST /orders

Description:
Creates a new order for a user.

Authentication:
Required.

Request body:
- user_id (string)
- product_id (string)
- quantity (number)

Response:
- 201 Created
- 400 Bad Request
- 401 Unauthorized

---

### 5. GET /orders/{id}

Description:
Fetches order details by order ID.

Authentication:
Required.

Response:
- 200 OK
- 401 Unauthorized
- 404 Not Found

---

## Error Handling

The API may return the following error codes:

400 Bad Request  
- The request payload is invalid or missing required fields.

401 Unauthorized  
- Authentication token is missing, expired, or invalid.

404 Not Found  
- The requested resource does not exist.

500 Internal Server Error  
- An unexpected server error occurred.

---

## Notes

- All responses are returned in JSON format.
- The API does not currently support pagination.
- Rate limiting is not documented.
