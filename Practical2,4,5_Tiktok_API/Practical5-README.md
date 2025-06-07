# TikTok Cloud Storage Integration with Supabase

This project upgrades the TikTok web application by replacing local file storage with **Supabase Cloud Storage**. The goal is to improve scalability, reliability, and performance by storing videos and thumbnails in the cloud, served via a global CDN.

## Why Use Cloud Storage?

Local file storage has limitations:

- Limited disk space
- No scalability across multiple servers
- Risk of data loss on crashes or redeployment
- No CDN support for global performance
- No built-in backups

Supabase Storage solves these issues by offering:

- Scalable, redundant, and CDN-delivered storage
- Public/private/custom access controls
- Easy frontend and backend integration
- Cost-effective usage-based pricing

## Project Overview

- **Backend**: Express + Prisma + Supabase Storage
- **Frontend**: Next.js (App Router)
- **Database**: PostgreSQL via Supabase
- **Storage**: Videos and thumbnails stored in Supabase buckets

## ⚙️ Backend Setup

### 1. Install Supabase Client

```bash
cd server
npm install @supabase/supabase-js
```

### 2. Configure Supabase Client

`src/lib/supabase.js`:

```js
const { createClient } = require('@supabase/supabase-js');

const supabaseUrl = process.env.SUPABASE_URL;
const supabaseKey = process.env.SUPABASE_SERVICE_KEY;

const supabase = createClient(supabaseUrl, supabaseKey);

module.exports = supabase;
```

### 3. Update `.env`

```ini
SUPABASE_URL=your-project-url
SUPABASE_SERVICE_KEY=your-service-key
SUPABASE_PUBLIC_KEY=your-public-key
SUPABASE_STORAGE_URL=your-project-url/storage/v1
```

### 4. Update Prisma Schema

Add storage paths to `Video` model:

```prisma
videoStoragePath String? @map("video_storage_path")
thumbnailStoragePath String? @map("thumbnail_storage_path")
```

Then run:

```bash
npx prisma migrate dev --name addStoragePaths
```

### 5. Update Controllers

- Modify `videoController.js` to upload/delete files using Supabase
- Store cloud URLs and paths in the database

### 6. Optional: Migrate Existing Videos

Run script:

```bash
cd server
node scripts/migrateVideosToSupabase.js
```

## Frontend Setup

### 1. Install Supabase Client

```bash
cd tiktok_frontend
npm install @supabase/supabase-js
```

### 2. Configure Client

`src/lib/supabase.js`:

```js
import { createClient } from '@supabase/supabase-js';

const supabase = createClient(
  process.env.NEXT_PUBLIC_SUPABASE_URL,
  process.env.NEXT_PUBLIC_SUPABASE_PUBLIC_KEY
);

export default supabase;
```

### 3. Update `.env.local`

```ini
NEXT_PUBLIC_SUPABASE_URL=your-project-url
NEXT_PUBLIC_SUPABASE_PUBLIC_KEY=your-public-key
```

### 4. Update Upload Logic

- Modify `uploadService.js` to upload files directly to Supabase
- Update `upload/page.jsx` to use new upload flow

### 5. Update VideoCard

- Ensure video URLs are built using Supabase paths

## Testing & Cleanup

- Confirm videos play correctly from Supabase URLs
- Run the migration script (if needed)
- Back up and remove old local uploads directory and file serving logic

## References

- Supabase Storage Docs
- Supabase JS Client
- TikTok Frontend Repo
- TikTok Server Repo