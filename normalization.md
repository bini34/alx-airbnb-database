### Objective

Apply normalization principles to ensure the database is in the third normal form (3NF), specifically modeling a one-to-one relationship between property and location.

### Normalization Steps

1. **Review Existing Schema**  
    The `property` table currently stores the `location` as a single `varchar` field. This design can lead to data redundancy and makes it difficult to enforce data integrity or perform location-based queries.

2. **Identify Redundancies and Violations**  
    Storing location as a single field violates normalization principles, as it combines multiple pieces of information (country, city, coordinates) into one column. This can result in update anomalies and redundant data.

3. **Adjust Database Design**  
    To achieve 3NF and enforce a one-to-one relationship, create a separate `location` table where each property has exactly one location, and each location belongs to exactly one property. Use `property_id` as both the primary key and foreign key in the `location` table:
    - `property_id` (Primary Key and Foreign Key referencing `property`)
    - `country`
    - `city`
    - `longitude`
    - `latitude`

    Remove the `location` column from the `property` table. Each property's location details are now stored in the `location` table, linked by `property_id`.

4. **Explanation**  
    By separating location details into their own table and enforcing a one-to-one relationship, each piece of information is stored only once, reducing redundancy. This design ensures that the database is in 3NF, as all non-key attributes are fully functionally dependent on the primary key, and there are no transitive dependencies.

### Example Table Structure

```sql
-- Property Table
CREATE TABLE property (
    property_id INT PRIMARY KEY,
    -- other property fields
);

-- Location Table (one-to-one with property)
CREATE TABLE location (
    property_id INT PRIMARY KEY,
    country VARCHAR(100),
    city VARCHAR(100),
    longitude DECIMAL(9,6),
    latitude DECIMAL(9,6),
    FOREIGN KEY (property_id) REFERENCES property(property_id)
);
```
