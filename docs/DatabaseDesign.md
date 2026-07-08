# Database Design

## Overview

The Incident Management System (IMS) uses MongoDB as its primary database. The database is designed to efficiently manage users, support tickets, and ticket discussions while maintaining clear relationships between entities. The application uses three primary collections:

- User
- Ticket
- Comment

---

## User Collection

The User collection stores information about every registered user in the system.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| _id | ObjectId | Unique identifier for the user |
| name | String | Full name of the user |
| email | String | Unique email address used for login |
| password | String | Hashed user password |
| role | String | User role (Customer, Support Engineer, Administrator) |
| createdAt | Date | Record creation timestamp |
| updatedAt | Date | Record update timestamp |

---

## Ticket Collection

The Ticket collection stores all incident reports created by customers.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| _id | ObjectId | Unique ticket identifier |
| title | String | Short title of the incident |
| description | String | Detailed incident description |
| status | String | Current ticket status |
| priority | String | Ticket priority |
| customer | ObjectId | Reference to the customer who created the ticket |
| assignedEngineer | ObjectId | Reference to the assigned support engineer |
| createdAt | Date | Ticket creation timestamp |
| updatedAt | Date | Ticket update timestamp |

### Ticket Status

- Open
- Assigned
- In Progress
- Resolved
- Closed

### Ticket Priority

- Low
- Medium
- High
- Critical

---

## Comment Collection

The Comment collection stores discussions related to a ticket.

### Fields

| Field | Type | Description |
|-------|------|-------------|
| _id | ObjectId | Unique comment identifier |
| message | String | Comment content |
| ticket | ObjectId | Reference to the associated ticket |
| user | ObjectId | Reference to the comment author |
| createdAt | Date | Comment creation timestamp |

---

## Relationships

### User → Ticket

- One customer can create many tickets.
- One support engineer can be assigned many tickets.

### Ticket → Comment

- One ticket can contain multiple comments.

### User → Comment

- One user can write multiple comments.

---

## Entity Relationship Overview

User
│
├── creates
│
▼
Ticket
│
├── has many
│
▼
Comment

Support Engineer
│
└── assigned to
    │
    ▼
 Ticket

---

## Database Design Considerations

- MongoDB is used because of its flexible document-based structure.
- References (ObjectId) are used to establish relationships between collections.
- Passwords are stored in hashed form for security.
- Automatic timestamps are maintained for auditing and tracking changes.
- The schema is designed to be modular and scalable, allowing future enhancements such as notifications, attachments, and activity logs without major structural changes.