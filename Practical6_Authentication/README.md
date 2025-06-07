# Authenticated Backend with Hono, TypeScript, Prisma & JWT

This practical demonstrates how to build a secure REST API using **TypeScript**, **Hono**, **PostgreSQL**, and **Prisma**, with a focus on **token-based authentication** using **JWT**. It includes user registration, login, and protected route access.

---

## What You'll Learn

- Email and password authentication with JWT
- Authorization using middleware
- Password hashing with Bun
- Securing API endpoints using JWT
- Prisma ORM for managing user and account data

---

## Prerequisites

- Basic knowledge of TypeScript, Node.js, REST APIs, and Prisma
- PostgreSQL installed
- Bun v1.x or later
- (Optional) Prisma extension in VS Code

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/rubcstswe/web102-hono-auth-jwt-prisma-forked.git
cd web102-hono-auth-jwt-prisma-forked
bun install
```

### 2. Set Up Prisma & Database

Update the Prisma schema as needed and push changes:

```bash
bunx prisma db push
bunx prisma generate
```

---

## Data Model

```prisma
model User {
  id           String    @id @default(uuid())
  email        String    @unique
  hashPassword String
  Account      Account[]
}

model Account {
  id      String @id @default(uuid())
  userId  String
  user    User   @relation(fields: [userId], references: [id])
  balance Int    @default(0)
}
```

- One user can have multiple accounts.
- Each account belongs to one user.

---

## API Endpoints

### Register (Public)

**POST** `/register`

Creates a user and stores a hashed password.

**Request Body:**
```json
{
  "email": "test@gmail.com",
  "password": "123456"
}
```

**Response:**
```json
{
  "message": "User created successfully"
}
```

### Login (Public)

**POST** `/login`

Authenticates the user and returns a JWT token.

**Request Body:**
```json
{
  "email": "test@gmail.com",
  "password": "123456"
}
```

**Response:**
```json
{
  "message": "Login successful",
  "token": "JWT_TOKEN"
}
```

### Protected Endpoint

**GET** `/protected/account/balance`

Returns the authenticated user's account balance.

**Headers:**
```makefile
Authorization: Bearer JWT_TOKEN
```

**Response:**
```json
{
  "data": {
    "Account": [
      {
        "balance": 0,
        "id": "75a34064-f8c4-4a7e-90dd-4958c452fbf4"
      }
    ]
  }
}
```

---

## Tech Stack

- **Hono** – Lightweight web framework
- **Prisma** – Type-safe ORM for database interaction
- **PostgreSQL** – Relational database
- **Bun** – Runtime environment and build tool
- **JWT** – Token-based authentication

---

## Security Notes

- Passwords are **hashed** using `Bun.password.hash` (bcrypt algorithm)
- JWT tokens are signed with a **secret key** and expire after 60 minutes
- Protected routes are secured using `jwt` middleware from Hono
- Do **not hardcode** the secret key in production; use `.env` or secure storage

---

## Project Structure (Key Files)

```bash
src/
├── index.ts     # API routes and middleware
├── prisma/      # Prisma schema and client
├── models/      # (Optional) For expanding model logic
.env             # Environment variables
```

---

## Testing the API

Use tools like **Postman** or **curl** to test:

```bash
# Register
curl -X POST http://localhost:3000/register \
  -H "Content-Type: application/json" \
  -d '{"email":"test@gmail.com","password":"123456"}'

# Login
curl -X POST http://localhost:3000/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@gmail.com","password":"123456"}'

# Get balance (replace TOKEN)
curl -X GET http://localhost:3000/protected/account/balance \
  -H "Authorization: Bearer TOKEN"
```

---

## Summary

This project helps you implement:
- Secure registration and login
- Password hashing and JWT generation
- Authorization via middleware
- Real-world token-based API security

For future improvements, consider:
- Token refresh flow
- Role-based permissions
- Email verification