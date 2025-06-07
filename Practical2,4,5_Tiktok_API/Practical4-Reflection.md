# TikTok Clone Backend – Prisma & PostgreSQL Integration Reflection

## Main Concepts Applied

In this practical, I connected the TikTok backend server to a PostgreSQL database using Prisma ORM. I applied key backend development concepts including:

- Database integration by replacing temporary in-memory data with persistent PostgreSQL storage
- Schema definition and management using Prisma ORM
- Database relationships between users, videos, comments, likes, and follows
- Secure user authentication using bcrypt for password hashing
- JWT-based authorization for protecting API routes
- Middleware implementation for route protection
- Database seeding with test data to simulate a real social media environment
- RESTful API endpoints for user registration, login, and protected operations

## What I Learned

I learned how to create and configure a PostgreSQL database and connect it to a Node.js application using Prisma. I now understand how to:

- Set up and configure PostgreSQL database with proper user permissions
- Define Prisma schema models with relationships and constraints
- Run database migrations and generate Prisma Client for database operations
- Hash passwords securely using bcrypt before storing in database
- Create and verify JWT tokens for user authentication
- Apply middleware to protect routes and verify user authorization
- Seed databases with realistic test data for development and testing
- Structure backend applications with proper separation of concerns

This helped me understand how modern backend applications handle data persistence, user authentication, and API security in production environments.

## Challenges and How I Solved Them

**Challenge 1: Prisma Schema Design and Relationships**
- **Problem:** I had difficulty setting up Prisma schema correctly and ensuring all relationships between users, videos, comments, likes, and follows worked as expected
- **Solution:** I solved this by carefully studying the Prisma documentation, understanding foreign key relationships, and testing each model step by step through migrations to ensure data integrity

**Challenge 2: JWT Authentication Implementation**
- **Problem:** I had trouble implementing token-based authentication correctly, including proper token generation, verification, and middleware integration
- **Solution:** I solved this by ensuring the JWT secret and expiry time were properly configured in the environment file, and implementing middleware that correctly verifies tokens before accessing protected routes

## Conclusion

This practical gave me comprehensive experience in building a full-featured backend application connected to a real database. Key achievements include:

- Understanding how to integrate PostgreSQL with Node.js applications using Prisma ORM
- Learning to implement secure authentication and authorization systems
- Gaining experience with database design, relationships, and migrations
- Building confidence in API security and middleware implementation
- Understanding the importance of environment configuration and secrets management

Overall, this practical significantly enhanced my backend development skills and provided valuable experience with modern database management and security practices. I now feel confident using Prisma for data management and implementing authentication systems in real-world projects where both database persistence and security are critical requirements.