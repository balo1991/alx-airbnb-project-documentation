# Airbnb Clone Backend Requirements

This document specifies the **technical and functional requirements** for the backend of the Airbnb Clone project.

---

## 1. User Authentication

### Functional Requirements
- Allow users to **register** with name, email, password, and role (guest/host/admin).
- Enable **login** with JWT-based session management.
- Provide **secure password storage** using hashing.
- Support **logout** and token invalidation.
- Allow users to **retrieve profile info** (`/me`).

### API Endpoints
- `POST /api/auth/register`
- `POST /api/auth/login`
- `POST /api/auth/logout`
- `GET /api/auth/me`

### Input/Output

```json
// Register Request
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "securePass123",
  "role": "host"
}

// Register Response
{
  "id": 1,
  "name": "John Doe",
  "email": "john@example.com",
  "role": "host",
  "created_at": "2025-09-04T12:00:00Z"
}

// Login Request
{
  "email": "john@example.com",
  "password": "securePass123"
}

// Login Response
{
  "token": "jwt_token_string",
  "expires_in": 86400
}
Validation Rules
Email must be unique and valid format.

Password: minimum 8 characters, at least 1 uppercase letter, and 1 number.

Role must be one of [guest, host, admin].

Performance
Authentication responses must return in <200ms.

Session tokens expire after configurable time (default: 24h).

2. Property Management
Functional Requirements
Hosts can create, update, and delete property listings.

Properties include details: title, description, price, location, amenities, and availability.

Guests can view and search property listings.

API Endpoints
POST /api/properties

GET /api/properties

GET /api/properties/{id}

PUT /api/properties/{id}

DELETE /api/properties/{id}

Input/Output
json
Copy code
// Create Property Request
{
  "title": "Cozy Apartment",
  "description": "Near city center",
  "price_per_night": 100,
  "location": "Paris",
  "amenities": ["WiFi", "TV"],
  "availability": true
}

// Property Response
{
  "id": 101,
  "title": "Cozy Apartment",
  "price_per_night": 100,
  "location": "Paris",
  "availability": true
}
Validation Rules
Price must be > 0.

Location string is required.

Availability must be boolean.

Performance
Property search must return results within 500ms for up to 10,000 listings.

3. Booking System
Functional Requirements
Guests can book available properties.

System prevents double-booking by checking availability.

Hosts can approve or decline booking requests.

API Endpoints
POST /api/bookings

GET /api/bookings/{id}

GET /api/users/{id}/bookings

PUT /api/bookings/{id}/status

Input/Output
json
Copy code
// Booking Request
{
  "user_id": 5,
  "property_id": 101,
  "start_date": "2025-09-10",
  "end_date": "2025-09-15"
}

// Booking Response
{
  "id": 201,
  "status": "pending",
  "total_price": 500
}
Validation Rules
Start date must be before end date.

Booking duration must not exceed 90 days.

User cannot book their own property.

Performance
Must handle 100+ concurrent bookings without data inconsistency.

4. Payment Processing
Functional Requirements
Users must complete payment for confirmed bookings.

Integrate with third-party payment gateways (Stripe, PayPal).

Refunds available for eligible cancellations.

API Endpoints
POST /api/payments

GET /api/payments/{id}

POST /api/payments/refund

Input/Output
json
Copy code
// Payment Request
{
  "booking_id": 201,
  "amount": 500,
  "payment_method": "credit_card"
}

// Payment Response
{
  "id": 301,
  "status": "success",
  "transaction_id": "txn_12345"
}
Validation Rules
Payment amount must equal booking total.

Only valid payment methods accepted.

Refunds only for eligible cancellations.

Performance
Payment requests must process within <3s.

99.9% availability for payment API.

5. Reviews & Ratings
Functional Requirements
Guests can leave reviews and ratings after completed stay.

Reviews are linked to both user and property.

Average ratings should display on property listings.

API Endpoints
POST /api/reviews

GET /api/reviews/property/{id}

GET /api/reviews/user/{id}

Input/Output
json
Copy code
// Review Request
{
  "user_id": 5,
  "property_id": 101,
  "rating": 4,
  "comment": "Great place, very clean!"
}

// Review Response
{
  "id": 401,
  "rating": 4,
  "comment": "Great place, very clean!",
  "created_at": "2025-09-04T13:00:00Z"
}
Validation Rules
Rating must be between 1–5.

Comment optional, max 500 characters.

User must have a completed booking before review.

Performance
Aggregated ratings must be calculated in real time (<200ms).

6. Admin Monitoring
Functional Requirements
Admins can view system-wide bookings, payments, and user activities.

Admins can block/unblock users or properties.

Generate reports on revenue and usage.

API Endpoints
GET /api/admin/users

GET /api/admin/properties

GET /api/admin/bookings

GET /api/admin/payments

PUT /api/admin/users/{id}/block

PUT /api/admin/properties/{id}/block

Input/Output
json
Copy code
// Block User Response
{
  "id": 5,
  "status": "blocked"
}
Validation Rules
Only admin role can access these endpoints.

Blocked users cannot log in or book properties.

Performance
Admin dashboards must load under 1s for up to 100,000 records.

