# TikTok REST API – Node.js Backend

This project implements a RESTful API backend for a TikTok-style application using **Node.js** and **Express**. The API supports operations for videos, users, comments, likes, and followers. It is designed to connect with a Next.js frontend and follows REST principles using proper HTTP methods and route structures.

## Project Setup

### 1. Create and initialize your backend project:

```bash
mkdir -p server
cd server
npm init -y
```

### 2. Install dependencies:

```bash
npm install express cors morgan body-parser dotenv
npm install --save-dev nodemon
```

### 3. Create project structure:

```
/server
  /src
    /controllers
    /routes
    /models
    /middleware
    /utils
    app.js
    server.js
  .env
```

### 4. Configuration Steps:

- Add environment variables in `.env` (e.g., PORT=3000)
- Set up your Express app in `src/app.js`
- Create server entry in `src/index.js`
- Add scripts to `package.json`:

```json
"scripts": {
  "start": "node src/index.js",
  "dev": "nodemon src/index.js"
}
```

## API Overview

The API supports the following routes:

### Videos

- `GET /api/videos` – Get all videos
- `POST /api/videos` – Create a new video
- `GET /api/videos/:id` – Get video by ID
- `PUT /api/videos/:id` – Update a video
- `DELETE /api/videos/:id` – Delete a video
- `GET /api/videos/:id/comments` – Get video comments
- `GET /api/videos/:id/likes` – Get likes
- `POST /api/videos/:id/likes` – Like video
- `DELETE /api/videos/:id/likes` – Unlike video

### Users

- `GET /api/users` – Get all users
- `POST /api/users` – Create a new user
- `GET /api/users/:id` – Get user by ID
- `PUT /api/users/:id` – Update user
- `DELETE /api/users/:id` – Delete user
- `GET /api/users/:id/videos` – Get a user's videos
- `GET /api/users/:id/followers` – Get followers
- `POST /api/users/:id/followers` – Follow user
- `DELETE /api/users/:id/followers` – Unfollow user
- `GET /api/users/:id/following` – Get following users

### Comments

- `GET /api/comments` – Get all comments
- `POST /api/comments` – Create comment
- `GET /api/comments/:id` – Get comment by ID
- `PUT /api/comments/:id` – Update comment
- `DELETE /api/comments/:id` – Delete comment
- `GET /api/comments/:id/likes` – Get comment likes
- `POST /api/comments/:id/likes` – Like comment
- `DELETE /api/comments/:id/likes` – Unlike comment

## Data Storage

- Data is stored temporarily in **in-memory structures** (`src/models/index.js`)
- No database is used in this version

## Controllers and Routes

- Video logic: `src/controllers/videoController.js`, `routes/videos.js`
- User logic: `src/controllers/userController.js`, `routes/users.js`
- Comment logic: `src/controllers/commentController.js`, `routes/comments.js`

## Testing

Use Postman or `curl` to test endpoints:

```bash
curl -X GET http://localhost:3000/api/users
curl -X GET http://localhost:3000/api/videos
curl -X GET http://localhost:3000/api/videos/1/comments
```