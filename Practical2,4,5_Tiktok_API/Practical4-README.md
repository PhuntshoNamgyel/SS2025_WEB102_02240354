# TikTok Clone Backend – Prisma & PostgreSQL Integration

This project connects the TikTok backend server to a **PostgreSQL** database using **Prisma ORM**. It replaces in-memory data with persistent storage, adds authentication with password hashing, and secures REST API endpoints with JWT-based authorization.

## Objectives

- Set up a PostgreSQL database and user
- Configure Prisma ORM to connect and manage schema
- Store and retrieve user, video, and comment data from the database
- Implement password encryption and token-based authentication
- Secure protected API routes using middleware
- Seed the database with test users, videos, comments, likes, and follows

## Setup Instructions

### 1. Create PostgreSQL Database

```bash
sudo -u postgres psql
CREATE DATABASE tiktok_db;
CREATE USER tiktok_user WITH PASSWORD 'your_password';
\q
```

### 2. Set Up Prisma

```bash
npm install @prisma/client
npm install prisma --save-dev
npx prisma init
```

Update `.env`:

```env
DATABASE_URL="postgresql://tiktok_user:your_password@localhost:5432/tiktok_db?schema=public"
```

### 3. Define Your Prisma Schema

Update `prisma/schema.prisma` with the TikTok data model.

Then:

```bash
npx prisma migrate dev --name init
npx prisma generate
```

### 4. Create Prisma Client

File: `src/lib/prisma.js`

```js
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

export default prisma
```

## Authentication Setup

- Install required packages:

```bash
npm install bcrypt jsonwebtoken
```

- Create JWT middleware: `src/middleware/auth.js`
- Use JWT middleware to protect routes (e.g., for posting videos, comments)
- Update `.env`:

```env
JWT_SECRET=yourverylongandsecurerandomsecret
JWT_EXPIRE=30d
PORT=5000
NODE_ENV=development
```

## Controller Updates

Update controllers to use Prisma:

- `userController.js`: for registration, login, and user queries
- `videoController.js`: for fetching, creating, and interacting with videos
- `commentController.js`: for comment management

Use:
- **bcrypt** to hash passwords
- **jsonwebtoken** to create/verify tokens
- **Prisma Client** for database operations

Reference Code: TikTok_Server Repository

## Testing

Start server:

```bash
npm run dev
```

Use Postman to test:
- `/register` – Create new user
- `/login` – Authenticate and receive token
- Use the token in `Authorization` header to access protected endpoints

## Seed the Database

- Create `prisma/seed.js` with logic to populate:
  - 10 users
  - 50 videos
  - 200 comments
  - 300 video likes
  - 150 comment likes
  - 40 follow relationships

- Add seed script in `package.json`:

```json
"scripts": {
  "dev": "nodemon src/index.js",
  "start": "node src/index.js",
  "seed": "node prisma/seed.js"
}
```

- Run the script:

```bash
npm install bcrypt
npm run seed
```

## Key Concepts

- **Database Design**: tables, relationships, indexes, foreign keys
- **ORM (Prisma)**: model definitions, migrations, transactions
- **Security**: password hashing, JWT tokens, protected routes
- **Testing**: Postman for registration, login, and protected access

## Resources

- Prisma Docs
- PostgreSQL Docs
- JWT Introduction