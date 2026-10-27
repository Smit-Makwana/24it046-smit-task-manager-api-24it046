# Task Manager API (MongoDB + Mongoose)

A RESTful Task Management API built using **Node.js**, **Express.js**, **MongoDB**, and **Mongoose**. This project demonstrates CRUD operations, MongoDB integration, schema validation, middleware, request logging, and error handling.

---

## Objective

Develop a RESTful backend server that supports:

- Create Task
- Read All Tasks
- Read Task by ID
- Update Task
- Delete Task

The project also includes:

- MongoDB Integration using Mongoose
- Schema Validation
- Global Logging Middleware
- Content-Type Validation Middleware
- Route-specific Middleware
- Global Error Handling Middleware
- 404 Not Found Handler

---

## Technologies Used

- Node.js
- Express.js
- MongoDB
- Mongoose
- dotenv
- VS Code
- Thunder Client

---

## Project Structure

```text
task-manager-api/
│── models/
│   └── Task.js
│── node_modules/
│── .env
│── .env.example
│── .gitignore
│── package.json
│── package-lock.json
│── server.js
│── README.md
```

---

## Installation

Clone the repository

```bash
git clone https://github.com/Smit-Makwana/24it046-smit-task-manager-api-24it046.git
```

Move into the project folder

```bash
cd task-manager-api
```

Install dependencies

```bash
npm install
```

Create a `.env` file

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/taskdb
```

Start MongoDB

```bash
mongod
```

Start the server

```bash
npm start
```

Server runs at

```
http://localhost:5000
```

---

## MongoDB Schema

```javascript
{
    title: String (required),
    description: String,
    completed: Boolean (default: false),
    priority: String (low | medium | high),
    createdAt: Date (default: Date.now)
}
```

---

## API Endpoints

### Get All Tasks

**GET**

```
http://localhost:5000/tasks
```

---

### Get Task by ID

**GET**

```
http://localhost:5000/tasks/:id
```

---

### Create Task

**POST**

```
http://localhost:5000/tasks
```

Request Body

```json
{
    "title":"Learn MongoDB",
    "description":"Practical 5",
    "priority":"high"
}
```

---

### Update Task

**PUT**

```
http://localhost:5000/tasks/:id
```

Request Body

```json
{
    "title":"Learn Express",
    "completed":true
}
```

---

### Delete Task

**DELETE**

```
http://localhost:5000/tasks/:id
```

---

## Middleware Used

### Logging Middleware

Logs every incoming request with:

- HTTP Method
- Request URL
- Timestamp

Example

```
GET /tasks - 2026-08-07T10:15:25.123Z
```

---

### Content-Type Middleware

Ensures POST and PUT requests use JSON.

Returns:

```
400 Bad Request
```

if Content-Type is not `application/json`.

---

### Route Validation Middleware

Validates MongoDB ObjectId before database operations.

Returns:

```
400 Bad Request
```

for invalid IDs.

---

### Global Error Handler

Handles:

- Validation Errors
- Invalid ObjectId
- Internal Server Errors

Example Response

```json
{
    "success": false,
    "message": "Validation Error"
}
```

---

### 404 Handler

Returns

```json
{
    "error":"Route Not Found"
}
```

for undefined routes.

---

## Mongoose Features Used

- MongoDB Connection
- Schema Design
- Required Fields
- Default Values
- Enum Validation
- Model Methods
- Validation Errors

---

## HTTP Status Codes

| Status Code | Meaning |
|------------|---------|
| 200 | OK |
| 201 | Created |
| 400 | Bad Request |
| 404 | Not Found |
| 500 | Internal Server Error |

---

## Testing

The API was tested using **Thunder Client**.

Requests Tested:

- POST /tasks
- GET /tasks
- GET /tasks/:id
- PUT /tasks/:id
- DELETE /tasks/:id
- Validation Error
- Invalid ID
- Route Not Found

---

## Learning Outcomes

- Express.js Server Development
- MongoDB Integration
- Mongoose ODM
- Schema Design
- CRUD Operations
- REST API Development
- Middleware Pipeline
- Error Handling
- Environment Variables
- API Testing with Thunder Client

---

## Author

**Smit Makwana**

ID: 24IT046  
B.Tech Information Technology  
CHARUSAT University