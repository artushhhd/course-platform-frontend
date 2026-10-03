# Course Platform Frontend

Next.js 16 client for a Laravel course-platform API.

**Backend:** https://github.com/artushhhd/course-platform-backend

## What this project demonstrates

- Next.js App Router with plain JavaScript
- Centralized API integration
- Authentication flows
- Course CRUD and media upload UX
- Likes and comments
- Role-aware administration UI
- Backend-driven authorization

## Tech Stack

- Next.js 16
- React 19
- JavaScript
- Tailwind CSS 4
- Native Fetch API
- Laravel Sanctum

## Application Areas

### User

- Registration and login
- Profile
- Course browsing
- Course details
- Likes and comments

### Course Management

- Create courses
- Upload course images
- Edit and delete owned courses
- Handle backend validation feedback

### Administration

- Course moderation
- Course approval
- User management
- Account blocking
- Administrative actions

The UI can hide unavailable actions for a better user experience, but the Laravel API is responsible for enforcing permissions.

## API Integration

All HTTP communication is centralized in:

~~~text
lib/api.js
~~~

It handles:

- Base URL configuration
- Bearer-token authentication
- JSON and FormData requests
- HTTP error handling
- 401 Unauthorized
- Token cleanup
- Media URL construction

Configure:

~~~env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
~~~

Environment-specific values stay outside application code.

## Application Structure

~~~text
app/
├── login/
├── profile/
├── Course/
├── addCourse/
├── admin/
└── layout.js

lib/
├── api.js
├── auth.js
└── ...
~~~

| Area | Responsibility |
|---|---|
| app/ | Routes and UI |
| lib/api.js | API communication |
| lib/auth.js | Authentication state |
| admin/ | Administrative UI |
| public/ | Static assets |

## Backend Contract

Representative endpoints:

~~~http
POST /api/register
POST /api/login
GET  /api/profile
POST /api/logout

GET    /api/courses
POST   /api/courses
PUT    /api/courses/{id}
DELETE /api/courses/{id}

POST /api/courses/{id}/like
POST /api/courses/{id}/comment
~~~

See the backend repository for complete endpoint and authorization details.

## Local Development

### Requirements

- Node.js
- npm
- Running Laravel backend

### Installation

~~~bash
npm install
~~~

Create .env.local:

~~~env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
~~~

Run:

~~~bash
npm run dev
~~~

Open http://localhost:3000.

### Production Build

~~~bash
npm run build
npm start
~~~

## Architecture

~~~text
Next.js App Router
      |
      +-- Pages / Components
      +-- Authentication
      +-- lib/api.js
              |
              v
       Laravel REST API
              |
              +-- RBAC + Policies + Validation
~~~

The frontend and backend remain separate applications so they can be developed and deployed independently.
