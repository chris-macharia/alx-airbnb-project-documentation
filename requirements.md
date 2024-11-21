# Airbnb Clone: Backend Technical and Functional Requirements

This document outlines the technical and functional requirements for three core backend features of the Airbnb Clone project: **User Authentication**, **Property Management**, and **Booking System**.

---

## 1. User Authentication

### Functional Requirements
- Users can register using email/password or third-party providers (e.g., Google/Facebook).
- Users can log in securely using their credentials or social accounts.
- Password reset functionality must be available.
- Token-based authentication for secure sessions.

### Technical Requirements
#### API Endpoints
- **POST /api/auth/register**
  - **Input**:
    ```json
    {
      "name": "John Doe",
      "email": "john.doe@example.com",
      "password": "password123"
    }
    ```
  - **Output (Success)**:
    ```json
    {
      "message": "User registered successfully.",
      "userId": "12345"
    }
    ```
  - **Output (Error)**:
    ```json
    {
      "error": "Email already exists."
    }
    ```

- **POST /api/auth/login**
  - **Input**:
    ```json
    {
      "email": "john.doe@example.com",
      "password": "password123"
    }
    ```
  - **Output**:
    ```json
    {
      "token": "jwt-token",
      "userId": "12345"
    }
    ```

- **POST /api/auth/reset-password**
  - **Input**:
    ```json
    {
      "email": "john.doe@example.com"
    }
    ```
  - **Output**:
    ```json
    {
      "message": "Password reset link sent to email."
    }
    ```

#### Validation Rules
- Email format must be valid.
- Password must be at least 8 characters long, containing a number and a special character.

#### Performance Criteria
- Registration and login requests should process within **500ms**.
- Password reset link generation must complete within **1 second**.

---

## 2. Property Management

### Functional Requirements
- Hosts can list properties with detailed information, such as:
  - Title, description, photos, price, location, and amenities.
- Hosts can edit or delete their property listings.
- Properties should be searchable and filterable by guests.

### Technical Requirements
#### API Endpoints
- **POST /api/properties**
  - **Input**:
    ```json
    {
      "title": "Modern Apartment",
      "description": "2-bedroom apartment in downtown.",
      "price": 120,
      "location": "New York, NY",
      "amenities": ["WiFi", "Air Conditioning", "Kitchen"],
      "photos": ["url1", "url2"]
    }
    ```
  - **Output (Success)**:
    ```json
    {
      "message": "Property listed successfully.",
      "propertyId": "67890"
    }
    ```
  - **Output (Error)**:
    ```json
    {
      "error": "Missing required fields."
    }
    ```

- **GET /api/properties?location=New%20York&price=100-150&amenities=WiFi**
  - **Output**:
    ```json
    [
      {
        "propertyId": "67890",
        "title": "Modern Apartment",
        "price": 120,
        "location": "New York, NY",
        "amenities": ["WiFi", "Air Conditioning"]
      }
    ]
    ```

#### Validation Rules
- Title must be between 5–100 characters.
- Price must be a positive number.
- Photos should be valid URLs.

#### Performance Criteria
- Property creation should complete within **1 second**.
- Filters must return results within **500ms**.

---

## 3. Booking System

### Functional Requirements
- Guests can book a property for specific dates.
- The system must check property availability before confirming a booking.
- Guests can view their past and upcoming bookings.

### Technical Requirements
#### API Endpoints
- **POST /api/bookings**
  - **Input**:
    ```json
    {
      "propertyId": "67890",
      "userId": "12345",
      "startDate": "2024-12-01",
      "endDate": "2024-12-10"
    }
    ```
  - **Output (Success)**:
    ```json
    {
      "message": "Booking confirmed.",
      "bookingId": "99887"
    }
    ```
  - **Output (Error)**:
    ```json
    {
      "error": "Property not available for selected dates."
    }
    ```

- **GET /api/bookings?userId=12345**
  - **Output**:
    ```json
    [
      {
        "bookingId": "99887",
        "propertyTitle": "Modern Apartment",
        "startDate": "2024-12-01",
        "endDate": "2024-12-10"
      }
    ]
    ```

#### Validation Rules
- Booking dates must not overlap with existing bookings.
- Start date must be before the end date.
- Both dates must be in the future.

#### Performance Criteria
- Booking confirmation should process within **1.5 seconds**.
- Fetching booking history must not exceed **700ms**.

---

