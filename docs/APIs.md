# API Design

## Overview

The Incident Management System follows RESTful API principles. The APIs are organized around resources such as authentication, users, tickets, comments, and dashboard statistics. All protected endpoints require JWT-based authentication.

---

## Authentication APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/auth/register | Register a new user |
| POST | /api/auth/login | Authenticate user and generate JWT |
| POST | /api/auth/logout | Logout the current user |

---

## User APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/users/profile | Get logged-in user profile |
| PATCH | /api/users/profile | Update user profile |
| GET | /api/users | Get all users (Admin only) |
| PATCH | /api/users/:id/role | Update user role (Admin only) |

---

## Ticket APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/tickets | Create a new ticket |
| GET | /api/tickets | Get all accessible tickets |
| GET | /api/tickets/:id | Get ticket details |
| PATCH | /api/tickets/:id | Update ticket |
| DELETE | /api/tickets/:id | Delete ticket |

---

## Ticket Assignment APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| PATCH | /api/tickets/:id/assign | Assign ticket to a support engineer |

---

## Ticket Status APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| PATCH | /api/tickets/:id/status | Update ticket status |

---

## Ticket Priority APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| PATCH | /api/tickets/:id/priority | Update ticket priority |

---

## Comment APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/tickets/:id/comments | Add a comment to a ticket |
| GET | /api/tickets/:id/comments | Get all comments for a ticket |

---

## Dashboard APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/dashboard | Retrieve dashboard statistics |

---

## Search & Filter

The ticket listing endpoint supports searching, filtering, and pagination.

### Search by Title

GET /api/tickets?search=laptop

### Filter by Status

GET /api/tickets?status=Open

### Filter by Priority

GET /api/tickets?priority=High

### Pagination

GET /api/tickets?page=1&limit=10

---

## Authentication & Authorization

- JWT authentication is required for all protected endpoints.
- Customers can access only their own tickets.
- Support Engineers can access only assigned tickets.
- Administrators have access to all resources.
- Role-based authorization is enforced on restricted endpoints.

---

## Response Format

All APIs follow a consistent JSON response structure.

### Success Response

```json
{
  "success": true,
  "message": "Operation completed successfully",
  "data": {}
}
```

### Error Response

```json
{
  "success": false,
  "message": "Resource not found",
  "error": {}
}
```