# KSU Logistics — IS 324 Project

A web-based package and document delivery system for King Saud University. The platform allows students and faculty to drop packages at campus logistics offices, track their status, and enables couriers to accept and deliver them.

## Tech Stack

- **Python** + **Flask** — Web framework
- **PostgreSQL** — Database (via `psycopg2`)
- **HTML/CSS** — Frontend templates
- **SHA-256** — Password hashing

## Features

- **Sign Up** — Register as Student, Faculty, or Courier with input validation (ID format, email, password length).
- **Login** — Credential verification using hashed passwords. Routes users to the appropriate dashboard based on role.
- **User Dashboard** — Drop a package by selecting a logistics office, entering dimensions, weight, and receiver ID. View all sent packages with tracking number, status, and timestamp.
- **Courier Panel** — Accept or deliver packages using sender ID and 16-digit tracking number. Updates package status in the database.
- **Package Tracking** — Each package gets a unique 16-digit tracking number with status flow: `Dropped → Accepted → Delivered`.

## Pages

| Page | Description |
|------|-------------|
| Sign Up | Register with name, ID, email, phone, and password |
| Login | Authenticate by role (Student / Faculty / Courier) |
| User Dashboard | Drop packages and view sent package history |
| Courier Dashboard | Accept or deliver packages by tracking number |

## Database Schema

**`users`** — Stores registered users

| Column | Type |
|--------|------|
| `id` | TEXT (PK) |
| `first_name` | TEXT |
| `last_name` | TEXT |
| `email` | TEXT |
| `phone` | TEXT |
| `password_hash` | TEXT |
| `user_class` | TEXT |

**`packages`** — Stores package records

| Column | Type |
|--------|------|
| `id` | SERIAL (PK) |
| `sender_id` | TEXT |
| `receiver_id` | TEXT |
| `office` | TEXT |
| `dimensions` | TEXT |
| `weight` | TEXT |
| `track_id` | TEXT |
| `timestamp` | TEXT |
| `status` | TEXT |

Tables are auto-created on first run.

## How to Run

### Prerequisites

- Python 3.x
- PostgreSQL

### Setup

```bash
# Install dependencies
pip install flask psycopg2

# Update the DATABASE_URL in app.py with your PostgreSQL connection string
# Example: "postgresql://user:password@localhost:5432/ksu_logistics"

# Run the app
python app.py
```


## Authors

- Abdulrahman Tariq Alawdah 
- Abdulilah Saeed Almusfir
- Abdullah Sulaiman Alaskar 
- Abdullah Ahmed Altuwayan
