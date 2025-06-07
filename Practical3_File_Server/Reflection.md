# File Upload Server Implementation Reflection

## Main Concepts Applied

In this practical, I created a full file upload system by connecting a React/Next.js frontend with a Node.js and Express backend. Key concepts applied include:

- **Multer middleware** - Handle file uploads on the server with file storage management
- **File validation** - Configure file type and size validation on the server side
- **Express server setup** - Create robust backend API endpoints for file handling
- **Frontend-backend communication** - Send requests directly from React to Express server
- **Axios integration** - Track upload progress and handle HTTP requests
- **CORS configuration** - Enable secure communication between frontend and backend

---

## What I Learned

I learned how to properly handle file uploads in a full-stack application:

### Backend Knowledge
- How to use Multer to parse multipart form data
- Validate files and save them securely on the server
- Set up proper error handling for file upload operations

### Frontend Skills
- Send form data using `FormData` for file uploads
- Track upload progress with Axios and provide real-time feedback
- Handle server responses and display appropriate user messages

### Full-Stack Integration
- How CORS works and why it's important when frontend and backend run on different ports
- Proper configuration for seamless client-server communication

---

## Challenges and How I Solved Them

### Challenge 1: CORS Errors
- **Problem:** Frontend couldn't communicate with backend due to cross-origin restrictions
- **Solution:** I used the `cors` middleware in the Express server and allowed requests from `http://localhost:3000`

### Challenge 2: Frontend-Backend Endpoint Connection
- **Problem:** Frontend wasn't pointing to the correct backend endpoint
- **Solution:** I updated the Axios POST URL in the form to `http://localhost:8000/api/upload`, ensuring proper communication between frontend and backend

---

## Conclusion

This practical helped me understand how to build and connect the frontend and backend parts of a file upload system. Key achievements include:

- Gained real experience with tools like Express, Multer, and Axios
- Learned how to handle file validation and upload progress tracking
- Mastered cross-origin request handling and API integration
- Improved confidence in working with backend APIs
- Enhanced skills in integrating backend services smoothly with frontend interfaces

Overall, this practical provided valuable full-stack development experience and strengthened my understanding of client-server architecture in modern web applications.