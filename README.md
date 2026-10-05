# Course Platform — Frontend

Next.js 16 / React 19 frontend for a Laravel course-platform API.

**Backend:** https://github.com/artushhhd/course-platform-backend

## Highlights

- Next.js App Router
- React 19 with JavaScript
- Centralized API client
- Authentication flows
- Course CRUD and image upload
- Likes and comments
- Role-aware administration UI
- Backend-driven authorization
- API validation and error handling

## Stack

Next.js 16 · React 19 · JavaScript · Tailwind CSS 4 · Fetch API · Laravel Sanctum

## API Integration

All HTTP communication is centralized in `lib/api.js` for API configuration, bearer tokens, JSON/FormData requests, HTTP errors, 401 handling, token cleanup, and media URLs.

```env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
```

## Architecture

```text
Next.js App Router
  -> Routes / Components
  -> Authentication / Administration
  -> lib/api.js
       |
       v
  Laravel REST API
  -> Sanctum / Policies / Validation
```

The frontend handles UX; the Laravel API remains the security boundary.

## Run Locally

```bash
npm install
npm run dev
```

Production build:

```bash
npm run build
npm start
```
