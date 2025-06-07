# TikTok Cloud Storage Integration with Supabase Reflection

## Main Concepts Applied

In this practical, I replaced local video and thumbnail storage in the TikTok web application with cloud storage using **Supabase**. I applied key cloud storage integration concepts including:

- Cloud storage migration from local file system to Supabase Storage
- Full-stack integration with both **backend (Express and Prisma)** and **frontend (Next.js)**
- Media file management using Supabase cloud buckets
- Database schema updates to store cloud storage paths
- Upload logic modification to use Supabase's storage API
- Public URL generation for video playback through CDN delivery
- Environment configuration for secure API key management
- File upload workflows for scalable media handling

## What I Learned

I learned how to use **Supabase Storage** to store media files and serve them through a CDN. I now understand how to:

- Configure Supabase clients for both backend and frontend applications
- Upload files securely to cloud storage buckets
- Generate and manage public URLs for media access
- Link uploaded file paths to database entries using Prisma
- Understand the differences between local storage and cloud storage in terms of scalability, reliability, and performance
- Implement proper environment variable configuration for cloud services
- Handle file migration from local storage to cloud storage

This helped me understand how modern web applications manage large media files effectively and the benefits of using cloud storage solutions over traditional local file systems.

## Challenges and How I Solved Them

**Challenge 1: File Upload and URL Access Configuration**
- **Problem:** I had difficulty correctly uploading files from the frontend to Supabase and ensuring that the returned URLs were publicly accessible for video playback
- **Solution:** I solved this by carefully reviewing Supabase's documentation, ensuring files were placed in public buckets with proper access policies, and verifying the URL generation process for public file access

**Challenge 2: Database Schema Updates and Path Storage**
- **Problem:** I had trouble updating the Prisma schema to store the new cloud storage paths and ensuring the upload logic properly saved these paths in the database
- **Solution:** I handled this by adding the required storage path fields to the Prisma schema, running proper database migrations, and updating the upload controllers to save both local database records and cloud storage paths

## Conclusion

This practical gave me comprehensive hands-on experience with integrating cloud storage into a full-stack web application. Key achievements include:

- Understanding how to migrate from local file handling to scalable cloud storage solutions
- Learning to implement Supabase Storage for efficient media content delivery
- Gaining experience with full-stack cloud service integration
- Building confidence in database schema updates and migration processes
- Understanding environment variable management and API security practices

Overall, this practical significantly enhanced my understanding of modern web application architecture and cloud service integration. I now feel confident implementing scalable file storage solutions using Supabase and understand the importance of cloud storage for building production-ready applications that can handle large media files efficiently.