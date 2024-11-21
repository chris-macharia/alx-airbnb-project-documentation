# Actors:
- Guest (End-user who books properties)
- Host (User who lists properties for rent)
- Admin (System administrator managing the platform)
- System (The backend system responsible for processing requests)<br>

# Use Cases:
1. User Registration:
Guest: Registers for an account.
System: Validates the information and creates a new user account.<br>
2. User Login/Logout:
Guest: Logs into their account or logs out.
System: Validates user credentials and manages session.<br>
3. Property Management:
Host: Adds, updates, and deletes property listings.
System: Manages the property details in the backend.<br>
4. Property Search:
Guest: Searches for available properties based on criteria (location, price, amenities, etc.).
System: Provides relevant search results.<br>
5. Booking Creation:
Guest: Books a property by selecting check-in/check-out dates and number of guests.
System: Processes the booking and confirms availability.<br>
6. Booking Confirmation:
Guest: Receives a booking confirmation upon successful booking.
System: Sends confirmation and stores the booking details.<br>
7. Payments:
Guest: Provides payment details and pays for the booking.
System: Processes payments securely and updates the booking status.<br>
8. Review and Rating:
Guest: Leaves a review and rating for a property after staying.
Host: Can respond to reviews.
System: Stores and displays reviews.<br>
9. Admin Management:
Admin: Manages users, properties, and financial transactions.
System: Provides access to user and property data, and financial reports.<br>

# System Boundaries:
The System is the backend platform responsible for handling user requests and interactions, including property management, booking, payments, and user data.
