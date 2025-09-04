#  Backend Requirements Specification 

##  Objective
This document defines the **technical and functional requirements** for three key backend features:  

1.  User Authentication  
2.  Property Management  
3.  Booking System  

Each feature includes **API endpoints, input/output specifications, validation rules, and performance criteria**.  


##  1. User Authentication

### Functional Requirements
- Allow users (guests, hosts, admins) to register, log in, and log out.  
- Secure password storage using hashing.  
- Use JWT-based tokens for authentication and session management.  

### API Endpoints
| Method | Endpoint              | Description                 |
|--------|-----------------------|-----------------------------|
| POST   | `/api/auth/register`  | Register a new user         |
| POST   | `/api/auth/login`     | Authenticate and issue token |
| POST   | `/api/auth/logout`    | Invalidate session/token    |

### Input / Output Example
**Register Request**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "StrongP@ss123",
  "role": "guest"
}
