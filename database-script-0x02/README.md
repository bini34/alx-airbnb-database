# AirBnB Database Sample Data

This directory contains SQL scripts to populate the AirBnB database schema with sample data for development and testing purposes.

## Files
- `seed.sql`: SQL INSERT statements to add sample data for all main entities (User, Property, Location, Booking, Payment, Review, Message).

## Usage
1. Ensure the database schema is created (see `../database-script-0x01/schema.sql`).
2. Run `seed.sql` in your SQL database to insert sample data.

## Sample Data Overview
- Multiple users (guests, hosts, admin)
- Properties with associated locations
- Bookings and payments reflecting real-world scenarios
- Reviews and messages between users

## Notes
- UUIDs are used for all primary keys.
- Data is designed to reflect realistic relationships and constraints.

## License
MIT
