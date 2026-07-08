# Project Architecture

## Overview

The Incident Management System follows a modular three-tier architecture consisting of the Presentation Layer, Application Layer, and Data Layer. This architecture promotes separation of concerns, making the application easier to maintain, test, and scale.

---

## Architecture Overview

Frontend (React)
        │
        ▼
REST APIs
        │
        ▼
Backend (Node.js + Express)
        │
        ▼
MongoDB Database

---

## Backend Folder Structure

backend/
│
└── src/
    ├── config/
    ├── controllers/
    ├── middleware/
    ├── models/
    ├── routes/
    ├── services/
    ├── validations/
    ├── utils/
    ├── docs/
    ├── app.js
    └── server.js

---

## Folder Responsibilities

### config/

Contains application configuration files such as database connection, environment variables, and Swagger configuration.

### controllers/

Handles incoming HTTP requests, validates input, calls business logic, and returns API responses.

### middleware/

Contains middleware functions such as authentication, authorization, error handling, and request validation.

### models/

Defines MongoDB schemas and models using Mongoose.

### routes/

Defines REST API endpoints and maps requests to their respective controllers.

### services/

Contains the business logic of the application, keeping controllers lightweight and maintainable.

### validations/

Stores request validation schemas to ensure incoming data is valid before processing.

### utils/

Contains reusable helper functions and utility methods.

### docs/

Stores Swagger API documentation files.

### app.js

Configures the Express application, middleware, and routes.

### server.js

Starts the server and establishes the database connection.

---

## Frontend Folder Structure

frontend/
│
└── src/
    ├── api/
    ├── assets/
    ├── components/
    ├── context/
    ├── hooks/
    ├── layouts/
    ├── pages/
    ├── routes/
    ├── services/
    ├── utils/
    └── App.jsx

---

## Design Principles

- Modular architecture
- Separation of concerns
- RESTful API design
- Role-Based Access Control (RBAC)
- Scalable folder organization
- Centralized error handling
- Reusable components and services