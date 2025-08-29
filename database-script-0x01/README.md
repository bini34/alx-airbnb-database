# AirBnB Database Schema

This project defines the database schema for an AirBnB-like platform, supporting users, properties, bookings, payments, reviews, and messaging. The schema is normalized to 3NF and optimized for data integrity and performance.

## Entities and Relationships

### User
- `user_id`: UUID, Primary Key
- `first_name`, `last_name`: Required
- `email`: Unique, Required
- `password_hash`: Required
- `phone_number`: Optional
- `role`: guest, host, or admin
- `created_at`: Timestamp

### Property
- `property_id`: UUID, Primary Key
- `host_id`: Foreign Key to User
- `name`, `description`: Required
- `pricepernight`: Required
- `created_at`, `updated_at`: Timestamps

### Location (One-to-One with Property)
- `property_id`: UUID, Primary Key & Foreign Key to Property
- `country`, `city`, `longitude`, `latitude`: Required

### Booking
- `booking_id`: UUID, Primary Key
- `property_id`: Foreign Key to Property
- `user_id`: Foreign Key to User
- `start_date`, `end_date`, `total_price`, `status`: Required
- `created_at`: Timestamp

### Payment
- `payment_id`: UUID, Primary Key
- `booking_id`: Foreign Key to Booking
- `amount`, `payment_method`: Required
- `payment_date`: Timestamp

### Review
- `review_id`: UUID, Primary Key
- `property_id`: Foreign Key to Property
- `user_id`: Foreign Key to User
- `rating`: Integer (1-5)
- `comment`: Required
- `created_at`: Timestamp

### Message
- `message_id`: UUID, Primary Key
- `sender_id`, `recipient_id`: Foreign Keys to User
- `message_body`: Required
- `sent_at`: Timestamp

## Constraints & Indexes
- Unique constraint on user email
- Foreign key constraints for all relationships
- Check constraints for ENUM-like fields (role, status, payment_method, rating)
- Indexes on frequently queried columns (email, property_id, booking_id, user_id)

## Usage
- The schema is defined in `schema.sql`.
- Run the script in your SQL database to create all tables and constraints.

## Normalization
- The schema is normalized to 3NF.
- Location details are separated into a dedicated table with a one-to-one relationship to Property.

## License
MIT
