# Richardson Maturity Model Evaluation

## Student Details

**Name:** Kalpesh Gausvami

**Subject:** Advanced Web Development Frameworks

**Practical:** Week 4 – Richardson Maturity Model Evaluation

---

# API Overview

The Task Management API is developed using **Node.js** and **Express.js**.

Available Endpoints

| Method | Endpoint | Description |
|---------|----------|-------------|
| GET | /tasks | Get all tasks |
| POST | /tasks | Create a new task |
| PUT | /tasks/:id | Update an existing task |
| DELETE | /tasks/:id | Delete a task |

---

# Richardson Maturity Model Evaluation

| Level | Criterion | Does API Satisfy? | Evidence |
|--------|-----------|-------------------|----------|
| Level 0 | Single endpoint service | ❌ No | The API uses multiple resource URLs instead of a single endpoint. |
| Level 1 | Resources identified using URIs | ✅ Yes | Separate URLs like `/tasks` and `/tasks/:id` are used. |
| Level 2 | Uses proper HTTP methods and status codes | ✅ Yes | Uses GET, POST, PUT, DELETE with 200, 201, 404, and 500 status codes. |
| Level 3 | Uses HATEOAS links | ❌ No | HATEOAS links are not implemented. |

---

# Evidence

### GET

```
GET /tasks
Status: 200 OK
```

Returns all tasks.

---

### POST

```
POST /tasks
Status: 201 Created
```

Creates a new task.

---

### PUT

```
PUT /tasks/1
Status: 200 OK
```

Updates an existing task.

---

### DELETE

```
DELETE /tasks/1
Status: 200 OK
```

Deletes the task successfully.

---

### Error Response

```
GET /abc
Status: 404 Not Found
```

Returns

```json
{
    "error":"Route Not Found"
}
```

---

# Richardson Level Achieved

The Task Management API satisfies **Richardson Maturity Model Level 2** because:

- Resources have unique URLs.
- Correct HTTP methods are used.
- Appropriate HTTP status codes are returned.
- Middleware provides centralized error handling.

---

# HATEOAS Awareness (Level 3)

If the API were upgraded to Level 3, responses could include links like:

```json
{
    "id":1,
    "title":"Learn Express",

    "_links":{

        "self":"/tasks/1",

        "update":"/tasks/1",

        "delete":"/tasks/1",

        "allTasks":"/tasks"

    }
}
```

These links allow clients to discover available actions without hardcoding URLs.

---

# Why Most Production APIs Stop at Level 2

Most production REST APIs stop at **Level 2** because:

- It provides a clean REST architecture.
- Clients already know endpoint URLs from API documentation.
- Implementing HATEOAS increases response size and development complexity.
- Most frontend applications (React, Angular, Vue, Mobile Apps) do not require HATEOAS.

Therefore, Level 2 provides a good balance between simplicity, performance, and maintainability.

---

# Conclusion

The developed Task Management API successfully satisfies **Richardson Maturity Model Level 2**.

No code changes were required because:

- Correct REST endpoints were already implemented.
- Proper HTTP methods were used.
- Correct status codes were returned.
- Error handling middleware was implemented successfully.

Future enhancement would be adding HATEOAS links to achieve Level 3.