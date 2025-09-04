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
```


### Validation Rules

- Email must be unique and valid format.

- Password ≥ 8 characters, at least 1 uppercase, 1 number, 1 special character.

- Role ∈ {guest, host, admin}.

### Performance Criteria

- Login/Register requests ≤ 500ms.

- Handle ≥ 100 concurrent login requests reliably.


## 2. Property Management

### Functional Requirements
- Hosts can list, update, and remove properties.  
- Each property must include: **title, description, price, location, amenities, availability**.  
- Only property owners can modify their listings.

### API Endpoints  

| Method | Endpoint              | Description                    |
|--------|-----------------------|--------------------------------|
| POST   | `/api/properties`     | Add a new property (host only) |
| PUT    | `/api/properties/:id` | Update property details        |
| DELETE | `/api/properties/:id` | Remove/unlist property         |
| GET    | `/api/properties/:id` | Fetch single property details  |
| GET    | `/api/properties`     | Search/filter properties       |


### Input / Output Examples  

**Property Request**  
```json
{
  "title": "Cozy Apartment",
  "description": "2-bedroom apartment near city center",
  "price_per_night": 120,
  "location": "New York, USA",
  "amenities": ["WiFi", "Air Conditioning", "pet friendly"],
  "availability": {
    "start_date": "2025-09-15",
    "end_date": "2025-12-31"
  }
}
```
**Property Response**  
```json
{
  "status": "success",
  "property_id": "uuid",
  "message": "Property listed successfully"
}
```

### Validation Rules

- Title ≤ 100 characters.

- Price > 0.

- Dates must follow YYYY-MM-DD format, with end_date ≥ start_date.

- Only owners can update/remove their properties.

### Performance Criteria

- Search results ≤ 1 second for up to 1000 listings.

- System supports ≥ 10,000 active property listings.

## 3. Booking System  

### Functional Requirements  
- Guests can create booking requests for available properties.  
- Hosts must approve or decline booking requests.  
- Prevent double-booking.  
- Booking statuses: **pending, confirmed, declined, canceled**.  

---

### API Endpoints  

| Method | Endpoint                        | Description                  |
|--------|---------------------------------|------------------------------|
| POST   | `/api/bookings`                 | Create a new booking request |
| PUT    | `/api/bookings/:id/confirm`     | Host confirms booking        |
| PUT    | `/api/bookings/:id/decline`     | Host declines booking        |
| PUT    | `/api/bookings/:id/cancel`      | Guest cancels booking        |
| GET    | `/api/bookings/:id`             | Fetch booking details        |
| GET    | `/api/bookings/user/:user_id`   | Fetch bookings for a user    |

---

### Input / Output Examples  

**Booking Request**  
```json
{
  "property_id": "uuid",
  "guest_id": "uuid",
  "start_date": "2025-10-01",
  "end_date": "2025-10-07"
}
```

**Booking Response**
```json
{
  "status": "success",
  "booking_id": "uuid",
  "status_code": "pending",
  "message": "Booking request created"
}
```

### Validation Rules

- Dates must not overlap with existing confirmed bookings.

- End date > start date.

- Guests cannot book their own properties.

### Performance Criteria

- Booking actions ≤ 500ms.

- Support ≥ 1,000 concurrent booking requests without failure.
