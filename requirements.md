# Project Requirements Specifications for the Airbnb Clone Backend

🔑 Core Functionalities Specifications:

## 1. User Management

### User Authentication:

**Description:** Allow users to sign up/in as **guests** or **hosts**.

**API Endpoints:**

- _post(/auth/register):_ create user account
  - _Input:_
    - name
    - role
    - email
    - password
  - _Output:_
    - Auth token(JWT) or session cookie
  - _Validation rules:_
    - name: required, text
    - role: required, match Guest or Host,
    - email: required, email, unique
    - Password: required, length>5, content special chart
  - _Performance criteria:_
    - respond in less than 200ms
- _post(/auth/login):_ log user in
  - _Input:_
    - email
    - password
  - _Output:_
    - Auth token(JWT) or session cookie
  - _Validation rules:_
    - email: required, email, exist
    - Password: required
  - _Performance criteria:_
    - respond in less than 200ms

### Profile Management:

**Description:** Allow users to manage his/her profile informations including profile photos, contact info, and preferences.
**API Endpoints:**

- _post(/account/profile):_ Add profile details
  - _Input:_
    - name
    - date-of-birth
    - profile-image
    - username
  - _Output:_
    - updated informations
  - _Validation rules:_
    - name: optional, text
    - date-of-birth: optional, date,
    - profile-image: optional, file
    - username: optional, text
  - _Performance criteria:_
- _put(/acount/profile):_ Update profile informations. Get the same caractéristics as the post(/acount/profile) endpoint.

## 2. Property Listings Management

**Description:** Allow Hosts manage their properties.
**API Endpoints:**

- _post(/proerties):_ Add a property to host properties
  - _Input:_
    - title
    - description
    - location
    - price
    - amenities
    - availability
  - _Output:_
    - property detailed informations
  - _Validation rules:_
    - title: required, text
    - description: required, text
    - location: required, text
    - price: required, float
    - amenities: required, list of text
    - availability: required, boolean
  - _Performance criteria:_
- _put(/proerties/id):_ Update a property in host properties
  - _Input:_
    - title
    - description
    - location
    - price
    - amenities
    - availability
  - _Output:_
    - property detailed informations
  - _Validation rules:_
    - id: exist in properties
    - title: optional, text
    - description: optional, text
    - location: optional, text
    - price: optional, float
    - amenities: optional, list of text
    - availability: optional, boolean
  - _Performance criteria:_
- _delete(/proerties/id):_ Delete a specified property in host properties, only by hosts
  - _Input:_
  - _Output:_
    - property suppression confirmation
  - _Validation rules:_
    - id: exist in properties
  - _Performance criteria:_
- _get(/proerties):_ Retrieve all the host properties, only by hosts
  - _Input:_
  - _Output:_
    - a list of properties
  - _Validation rules:_
  - _Performance criteria:_
- _get(/proerties/id):_ Retrieve a property details
  - _Input:_
  - _Output:_
    - a list of properties
  - _Validation rules:_
    - id: exist in properties
  - _Performance criteria:_

## 3. Booking Management

**Description:** Allow Guests manage their Bookings.

**API Endpoints:**

- _post(/booking):_ Add a booking for a property

  - _Input:_
    - property_id
    - start_date
    - end_date
    - payment_method
  - _Output:_
    - Booking status
  - _Validation rules:_
    - property_id: required, exist in properties
    - start_date: required, date
    - end_date: required, date
    - The selected property is free between start_date and end_date
    - payment_method: required, text
  - _Performance criteria:_

- _get(/booking/id):_ Get the booking details

  - _Input:_
  - _Output:_
    - Booking detailled informations
  - _Validation rules:_
  - _Performance criteria:_

- _delete(/booking/id):_ Booking cancellation
  - _Input:_
  - _Output:_
    - Booking cancellation status
  - _Validation rules:_ The cancellation policy is respected
  - _Performance criteria:_
