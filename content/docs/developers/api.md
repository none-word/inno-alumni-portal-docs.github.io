+++
title = 'Api'
+++

# API Documentation - Donation

This document provides an overview of the endpoints available in the Donation Management API.

## Base URL

The base URL for all endpoints is `/donation`.

## Authentication

All endpoints in this API require authentication. The user must be logged in, and their token must be included in the request headers.

### Headers

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Endpoints

### 1. Get All Donations

#### `GET /`

**Description:** Retrieve a list of all donations made by the user.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      "id": "string",
      "user_id": "string",
      "message": "string",
      "created_at": "string",
      "user": {
        "id": "string",
        "username": "string",
        "email": "string"
      }
    },
    // ... (more donations)
  ]
  ```

### 2. Make Donation

#### `POST /`

**Description:** Make a new donation.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "message": "string"
  }
  ```

**Response:**
- Status Code: 201 Created
- Content Type: application/json
- Body:
  ```json
  {
    "status": 201,
    "detail": "Donation Successfully created",
    "data": {
      "id": "string",
      "user_id": "string",
      "message": "string",
      "created_at": "string",
      "user": {
        "id": "string",
        "username": "string",
        "email": "string"
      }
    }
  }
  ```

### 3. Get Admin Donation Message

#### `GET /admin`

**Description:** Retrieve the latest donation message of type "ADMIN".

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "user_id": "string",
    "message": "string",
    "created_at": "string"
  }
  ```

### 4. Update Admin Donation Message

#### `POST /admin`

**Description:** Update the donation message of type "ADMIN". If the message does not exist, it will be created.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "message": "string"
  }
  ```

**Response:**
- Status Code: 202 Accepted
- Content Type: application/json
- Body:
  ```json
  {
    "status": 202,
    "detail": "Donation Successfully created",
    "data": {
      "id": "string",
      "user_id": "string",
      "message": "string",
      "created_at": "string"
    }
  }
  ```

## Error Responses

- 401 Unauthorized: Missing or invalid authentication token.
- 404 Not Found: Resource not found.
- 422 Unprocessable Entity: Invalid input or missing required fields.
- 500 Internal Server Error: Server-side error.


# API Documentation - Elective Courses

## Base URL

The base URL for all endpoints is `/elective_course`.

## Authentication

All endpoints in this API require authentication. The user must be logged in, and their token must be included in the request headers.

### Headers

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Endpoints

### 1. Get All Elective Courses

#### `GET /`

**Description:** Retrieve a list of all available elective courses.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      "id": "string",
      "course_name": "string",
      "instructor_name": "string",
      "description": "string",
      "mode": "string"
    },
    // ... (more elective courses)
  ]
  ```

### 2. Get All Elective Courses by Admin

#### `GET /admin`

**Description:** Retrieve a list of all elective courses (admin access).

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      "id": "string",
      "course_name": "string",
      "instructor_name": "string",
      "description": "string",
      "mode": "string"
    },
    // ... (more elective courses)
  ]
  ```

### 3. Get Booked Elective Courses

#### `GET /booked`

**Description:** Retrieve a list of elective courses booked by the user.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      "id": "string",
      "course_name": "string",
      "instructor_name": "string",
      "description": "string",
      "mode": "string",
      "created_at": "string",
      "elective_course": {
        // elective course details
      }
    },
    // ... (more booked elective courses)
  ]
  ```

### 4. Get All Elective Requests

#### `GET /request`

**Description:** Retrieve a list of all elective course requests.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      "id": "string",
      "user": {
        // user details
      },
      "elective_course": {
        // elective course details
      },
      "status": "string",
      "created_at": "string"
    },
    // ... (more elective course requests)
  ]
  ```

### 5. Create Elective Course

#### `POST /`

**Description:** Create a new elective course.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "course_name": "string",
    "instructor_name": "string",
    "description": "string",
    "mode": "string"
  }
  ```

**Response:**
- Status Code: 201 Created
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "course_name": "string",
    "instructor_name": "string",
    "description": "string",
    "mode": "string"
  }
  ```

### 6. Bulk Create Elective Courses

#### `POST /bulk`

**Description:** Bulk create multiple elective courses.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  [
    {
      // elective course details
    },
    // ... (more elective courses)
  ]
  ```

**Response:**
- Status Code: 201 Created
- Content Type: application/json
- Body:
  ```json
  {
    "number_added": 5
  }
  ```

### 7. Update Elective Course

#### `PUT /`

**Description:** Update an existing elective course.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "course_name": "string",
    "instructor_name": "string",
    "description": "string",
    "mode": "string"
  }
  ```

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "course_name": "string",
    "instructor_name": "string",
    "description": "string",
    "mode": "string"
  }
  ```

### 8. Delete Elective Course

#### `DELETE /remove`

**Description:** Delete an elective course.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "course_name": "string",
    "instructor_name": "string",
    "description": "string",
    "mode": "string"
  }
  ```

### 9. Disconnect Elective Course Request

#### `DELETE /`

**Description:** Disconnect an elective course request.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "course_name": "string",
    "instructor_name": "string",
    "description": "string",
    "mode": "string"
  }
  ```

### 10. Request Elective Course

#### `POST /request`

**Description:** Request an elective course.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "course_id": "string"
  }
  ```

**Response:**
- Status Code: 201

Created
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "user_id": "string",
    "course_id": "string",
    "status": "string"
  }
  ```

### 11. Update Elective Request

#### `PATCH /`

**Description:** Update an elective course request.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "status": "string"
  }
  ```

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "user": {
      // user details
    },
    "elective_course": {
      // elective course details
    },
    "status": "string",
    "created_at": "string"
  }
  ```

# API Documentation - Obtain Pass

## Base URL

The base URL for all endpoints is `/request_pass`.

## Authentication

All endpoints in this API require authentication. The user must be logged in, and their token must be included in the request headers.

### Headers

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Endpoints

### 1. Get All Pass Requests

#### `GET /`

**Description:** Retrieve a list of all pass requests made by the user.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      "id": "string",
      "user_id": "string",
      "description": "string",
      "requested_date": "string",
      "guest_info": "string",
      "created_at": "string"
    },
    // ... (more pass requests)
  ]
  ```

### 2. Get All Pass Requests by Admin

#### `GET /admin`

**Description:** Retrieve a list of all pass requests (admin access).

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      "id": "string",
      "user": {
        // user details
      },
      "description": "string",
      "requested_date": "string",
      "guest_info": "string",
      "created_at": "string"
    },
    // ... (more pass requests)
  ]
  ```

### 3. Update Elective Request

#### `PATCH /`

**Description:** Update an existing pass request.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "status": "string"
  }
  ```

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "user": {
      // user details
    },
    "description": "string",
    "requested_date": "string",
    "guest_info": "string",
    "status": "string",
    "created_at": "string"
  }
  ```

### 4. Order Pass

#### `POST /`

**Description:** Create a new pass order.

**Request:**
- Headers: `Authorization`
- Body:
  ```json
  {
    "description": "string",
    "requested_date": "string",
    "guests": ["string", "string"]
  }
  ```

**Response:**
- Status Code: 201 Created
- Content Type: application/json
- Body:
  ```json
  {
    "status": 201,
    "detail": "Successfully created pass order",
    "data": {
      "id": "string",
      "user_id": "string",
      "description": "string",
      "requested_date": "string",
      "guest_info": "string",
      "created_at": "string"
    }
  }
  ```

### 5. Disconnect Pass Request

#### `DELETE /`

**Description:** Disconnect a pass request.

**Request:**
- Headers: `Authorization`

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "id": "string",
    "user_id": "string",
    "description": "string",
    "requested_date": "string",
    "guest_info": "string",
    "status": "string",
    "created_at": "string"
  }
  ```

Certainly! Here's the Markdown representation of the API documentation for the provided FastAPI code:

# API Documentation - User Authentication

## Base URL

The base URL for all endpoints is `/user`.

## Authentication

Authentication is required for certain endpoints. The user must be logged in, and their token must be included in the request headers.

### Headers

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Endpoints

### 1. Login Alumni

#### `POST /login`

**Description:** Login for alumni users.

**Request:**
- Body:
  ```json
  {
    "username": "string",
    "password": "string"
  }
  ```

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    "access_token": "string",
    "token_type": "bearer"
  }
  ```

### 2. Register Alumni Account

#### `POST /register`

**Description:** Register a new alumni account.

**Request:**
- Body:
  ```json
  {
    "name": "string",
    "email": "string",
    "password": "string",
    "confirm_password": "string"
  }
  ```

**Response:**
- Status Code: 201 Created
- Content Type: application/json
- Body:
  ```json
  {
    "status": 201,
    "message": "Successfully registered user"
  }
  ```

### 3. Register Admin Account

#### `POST /register-admin`

**Description:** Register a new admin account.

**Request:**
- Body:
  ```json
  {
    "name": "string",
    "email": "string",
    "password": "string"
  }
  ```

**Response:**
- Status Code: 201 Created
- Content Type: application/json
- Body:
  ```json
  {
    // user details
  }
  ```

### 4. Update Alumni Account

#### `POST /update`

**Description:** Update alumni account information.

**Request:**
- Body:
  ```json
  {
    // user details to update
  }
  ```

**Response:**
- Status Code: 201 Created
- Content Type: application/json
- Body:
  ```json
  {
    // updated user details
  }
  ```

### 5. Update Password

#### `POST /update-password`

**Description:** Update alumni account password.

**Request:**
- Body:
  ```json
  {
    "current_password": "string",
    "new_password": "string"
  }
  ```

**Response:**
- Status Code: 202 Accepted
- Content Type: application/json
- Body:
  ```json
  {
    "status": 202,
    "message": "Successfully updated password"
  }
  ```

### 6. Get Current Alumni

#### `GET /`

**Description:** Retrieve details of the currently logged-in alumni.

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  {
    // user details
  }
  ```

### 7. Get All Registered Alumni

#### `GET /all`

**Description:** Retrieve details of all registered alumni.

**Response:**
- Status Code: 200 OK
- Content Type: application/json
- Body:
  ```json
  [
    {
      // user details with statistics
    },
    // ... (more alumni)
  ]
  ```

### 8. Forgot Password

#### `POST /forgot-password`

**Description:** Request a password reset for a registered user.

**Request:**
- Body:
  ```json
  {
    "university_email": "string"
  }
  ```

**Response:**
- Status Code: 200 OK

### 9. Verify Account

#### `POST /verify-account`

**Description:** Verify a user's account.

**Request:**
- Body:
  ```json
  {
    "university_email": "string"
  }
  ```

**Response:**
- Status Code: 200 OK

### 10. Confirm Verification

#### `POST /confirm_verification`

**Description:** Confirm user verification.

**Request:**
- Body:
  ```json
  {
    "email": "string",
    "code": "string"
  }
  ```

**Response:**
- Status Code: 200 OK

### 11. Login with SSO

#### `GET /login_sso`

**Description:** Initiate login with Single Sign-On (SSO).

**Response:**
- Redirects to the SSO provider for authentication.

### 12. SSO Token Callback

#### `GET /token_sso`

**Description:** Callback endpoint for handling SSO token.

### 13. SSO User Callback

#### `GET /user_sso`

**Description:** Callback endpoint for handling SSO user information.

### 14. SSO Authentication Callback

#### `GET /callback`

**Description:** Callback endpoint for completing SSO authentication.
