# File Upload on the Server Application

This project implements a complete file upload system using a React/Next.js frontend and a Node.js/Express backend. It supports drag-and-drop uploading, file validation, upload progress tracking, and secure server-side storage using Multer.

---

## Backend Setup (Express Server)

### Step 1: Create Project Directory

```bash
mkdir file-upload-server && cd file-upload-server
npm init -y
```

### Step 2: Install Required Dependencies

```bash
npm install express cors multer morgan dotenv
```

**Dependencies:**
- **express** - server framework
- **cors** - to handle cross-origin requests
- **multer** - middleware for handling file uploads
- **morgan** - logging HTTP requests
- **dotenv** - to manage environment variables

### Step 3: Server Configuration

1. Create `server.js` with basic Express setup
2. Configure **Multer** for:
   - File storage
   - File type validation (e.g., PDF only)
   - File size limits
3. Add upload API endpoint in `server.js` using Multer
4. Set up error handling middleware after the routes
5. Configure CORS to allow requests from the frontend (e.g., localhost:3000)
6. Create a `.env` file to store server configuration if needed

---

## Frontend Update (React/Next.js)

### Step 1: Modify Form Component

1. Modify your `page.js` or form component:
   - Use `axios` to send a POST request to `http://localhost:8000/api/upload`
   - Update `onSubmit` to send the file using `FormData`

### Step 2: Add Enhanced Features

- Use `react-dropzone` for drag-and-drop file input
- Add validation for file type and size on the client side
- Use `axios.onUploadProgress` to track and display upload progress
- Update the preview section to show uploaded PDF file names

---

## How to Run the App

### Step 1: Start the Backend

```bash
node server.js
```

### Step 2: Start the Frontend

```bash
npm run dev
```
*(from your Next.js project)*

### Step 3: Test the Application

Open the upload form in the browser and test:
- Upload valid files (e.g., PDF)
- Check progress bar
- View success or error messages
- Confirm files are saved in the server's `uploads` directory

---

## Key Features

- Drag-and-drop file uploads
- File type and size validation
- Upload progress tracking
- Secure file handling with Multer
- Full client-to-server integration using Axios

---

## Reference Code

**GitHub:** https://github.com/syangche/Backend_Practicals.git