# User Stories – Airbnb Clone

## 🎯 Objective
This document translates the interactions from the **Use Case Diagram** into user stories with acceptance criteria.  
Each story captures the perspective of an actor (Guest, Host, or Admin) and the value they gain from the feature.

---

## 👥 User Stories with Acceptance Criteria

### 1. User Registration & Login
**Story**:  
As a **guest or host**, I want to **register and log in** so that I can access the platform and use its features.  

**Acceptance Criteria**:  
- **Given** I am a new user, **when** I provide valid details, **then** my account should be created.  
- **Given** I already have an account, **when** I log in with valid credentials, **then** I should be granted access.  
- **Given** I enter invalid credentials, **when** I try to log in, **then** I should see an error message.  

---

### 2. Search Properties
**Story**:  
As a **guest**, I want to **search for properties by location, price, and amenities** so that I can find the best match for my stay.  

**Acceptance Criteria**:  
- **Given** properties exist in the system, **when** I enter search criteria, **then** I should see matching properties.  
- **Given** no properties match my criteria, **when** I search, **then** I should see a “No results found” message.  

---

### 3. Book Property
**Story**:  
As a **guest**, I want to **book a property for specific dates** so that I can secure my accommodation.  

**Acceptance Criteria**:  
- **Given** a property is available, **when** I select dates and confirm booking, **then** my booking should be created with status `pending`.  
- **Given** the host confirms the booking, **when** I check my booking, **then** the status should be `confirmed`.  
- **Given** I cancel a booking, **when** I confirm cancellation, **then** the status should update to `canceled`.  

---

### 4. Make Payment
**Story**:  
As a **guest**, I want to **pay securely online using a credit card or PayPal** so that my booking is confirmed immediately.  

**Acceptance Criteria**:  
- **Given** I have a pending booking, **when** I provide valid payment details, **then** the payment should be processed successfully.  
- **Given** the payment is successful, **when** I check my booking, **then** the status should update to `confirmed`.  
- **Given** payment fails, **when** I retry or use another method, **then** the system should attempt to process again.  

---

### 5. Leave Review
**Story**:  
As a **guest**, I want to **leave a rating and review for a property I stayed at** so that I can share my experience with other travelers.  

**Acceptance Criteria**:  
- **Given** I have completed a booking, **when** I submit a rating (1–5) and comment, **then** the review should be saved and displayed on the property.  
- **Given** I did not complete a booking, **when** I try to leave a review, **then** the system should block the action.  

---

### 6. Manage Listings
**Story**:  
As a **host**, I want to **add, edit, or remove my property listings** so that I can keep my information up to date.  

**Acceptance Criteria**:  
- **Given** I am logged in as a host, **when** I add a listing with required details, **then** the property should be saved.  
- **Given** I update my listing, **when** I save changes, **then** the property should display updated details.  
- **Given** I delete my listing, **when** I confirm the action, **then** the property should no longer be available for booking.  

---

### 7. Manage Users
**Story**:  
As an **admin**, I want to **view and manage user accounts** so that I can ensure the platform is safe and free of fraud.  

**Acceptance Criteria**:  
- **Given** I am logged in as admin, **when** I view the user list, **then** I should see all registered users.  
- **Given** a user violates rules, **when** I deactivate their account, **then** the user should no longer be able to log in.  

---

### 8. Monitor Payments
**Story**:  
As an **admin**, I want to **monitor all payments on the platform** so that I can track transactions and resolve disputes.  

**Acceptance Criteria**:  
- **Given** I am logged in as admin, **when** I view the payment dashboard, **then** I should see all successful and failed payments.  
- **Given** a payment dispute occurs, **when** I investigate, **then** I should be able to view details linked to the booking and user.  

---
