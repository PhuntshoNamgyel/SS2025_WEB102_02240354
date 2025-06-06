# Social Media RESTful API (Node.js + Express)

This project is a backend REST API for a social media platform (similar to Instagram). It supports core features like users, posts, comments, likes, and followers. The API is designed using REST principles and implemented using Node.js and Express.

---

## Project Setup

### Step 1: Create Project and Initialize

```bash
mkdir social-media-api
cd social-media-api
npm init -y
```

### Step 2: Install Dependencies

```bash
npm install express morgan cors helmet
npm install nodemon --save-dev
```

### Step 3: Create Project Structure

```bash
/controllers
/routes
/middleware
/config
/utils
server.js
.env
.gitignore
```

### Step 4: Environment Configuration

Add to `.env`:

```ini
PORT=3000
```

Example `.gitignore`:

```bash
node_modules
.env
.DS_Store
```

### Step 5: Add Scripts to package.json

```json
"scripts": {
  "start": "node server.js",
  "dev": "nodemon server.js"
}
```

---

## Features Implemented

**RESTful API endpoints for:**
- Users
- Posts
- Comments
- Likes
- Followers

**Each resource includes routes to:**
- List all items
- Get one item
- Create an item
- Update an item
- Delete an item

---

## Mock Data

- Mock data is stored in `utils/mockData.js`
- Used to simulate a database while building endpoints

---

## Middleware

- **Error handling:** `middleware/errorHandler.js`
- **Async handler:** `middleware/async.js`
- **Response formatter (Content Negotiation):** `middleware/formatResponse.js`

---

## Controllers and Routes

- **Users:** `controllers/userController.js`, `routes/users.js`
- **Posts:** `controllers/postController.js`, `routes/posts.js`
- Similar structure for comments, likes, and followers

---

## API Documentation

- Create a folder `public` and add `docs.html`
- This file provides basic HTML documentation for your endpoints

---

## Run the API

To start the development server:

```bash
npm run dev
```

The server runs on `http://localhost:3000`

---

## Concepts Applied

- RESTful API design (GET, POST, PUT, DELETE)
- Proper status codes
- Content negotiation (JSON, XML support via middleware)
- Modular file structure
- Middleware and error handling
- Simple API documentation