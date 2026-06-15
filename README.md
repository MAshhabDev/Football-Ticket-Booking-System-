# Football Ticket Booking System - Database & SQL

A relational database design and SQL implementation for managing football match ticket bookings, enforcing data integrity constraints, and handling complex relational queries.

---

## 🛠️ Schema Architecture

### 1. Users Table
Handles user profiles and role-based restrictions.
* `user_id` (INT, Primary Key)
* `full_name` (VARCHAR, NOT NULL)
* `email` (VARCHAR, UNIQUE, NOT NULL)
* `role` (VARCHAR, CHECK: 'Ticket Manager', 'Football Fan')
* `phone_number` (VARCHAR)

### 2. Matches Table
Stores fixture listings, pricing, and live availability statuses.
* `match_id` (INT, Primary Key)
* `fixture` (VARCHAR, NOT NULL)
* `tournament_category` (VARCHAR, NOT NULL)
* `base_ticket_price` (DECIMAL, CHECK >= 0)
* `match_status` (VARCHAR, CHECK: 'Available', 'Selling Fast', 'Sold Out', 'Postponed')

### 3. Bookings Table
A transactional junction table linking users to specific match tickets.
* `booking_id` (INT, Primary Key)
* `user_id` (INT, Foreign Key -> Users)
* `match_id` (INT, Foreign Key -> Matches)
* `seat_number` (VARCHAR)
* `payment_status` (VARCHAR, CHECK: 'Pending', 'Confirmed', 'Cancelled', 'Refunded')
* `total_cost` (DECIMAL, CHECK >= 0)

---

## 💻 Core Concepts Demonstrated

* **Data Integrity:** Strict usage of `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, and `NOT NULL` constraints.
* **Domain Validation:** Implementation of `CHECK` constraints to restrict invalid inputs (e.g., negative prices, unsupported roles).
* **Advanced Querying:** Solved real-world business logics using multi-table `INNER/LEFT JOINS`, `Subqueries`, conditional handling (`COALESCE`), case-insensitive filters (`ILIKE`), and pagination (`LIMIT/OFFSET`).

---

## 🚀 Execution Guide

1. **Schema Initialization:** Execute the DDL table creation scripts in your PostgreSQL environment.
2. **Query Verification:** Run the `QUERY.sql` script to test and view outputs for all 7 required assignment queries.
