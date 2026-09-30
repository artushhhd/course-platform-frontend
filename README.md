# Course Platform Frontend

Next.js 16 frontend for a course platform backed by a Laravel REST API.

**Backend:** https://github.com/artushhhd/course-platform-backend

## Overview

The Course Platform is split into independent frontend and backend applications. This repository contains the Next.js client responsible for the user interface, authentication flows, API integration, course interactions, and administrative UI.

The application uses the Next.js App Router and plain JavaScript.

## Tech Stack

- Next.js 16
- React 19
- JavaScript
- Tailwind CSS 4
- Native Fetch API
- Laravel Sanctum

## Core Features

### Authentication

- Registration, login, and logout
- Token persistence
- Protected user flows
- Profile page
- Backend validation error handling
- Handling of invalid or expired authentication

### Courses

- Browse courses
- View course details
- Create courses
- Upload course images
- Edit and delete owned courses
- Like and unlike courses
- Add comments

### Administration

The admin area provides:

- Course moderation
- Course approval
- User management
- Account blocking
- Administrative actions

Frontend visibility is role-aware, while authorization is enforced by the Laravel API.

## API Integration

All backend communication is centralized in:

```text
lib/api.js
```

The API client handles:

- API base URL configuration
- Bearer-token authentication
- JSON and FormData requests
- HTTP error handling
- `401 Unauthorized` handling
- Token cleanup
- Media URL construction

Configure the backend URL with:

```env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
```

Environment-specific configuration is kept out of application code.

## Application Structure

```text
app/
├── page.js
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

public/
└── ...
```

| Part | Responsibility |
|---|---|
| `app/` | Pages and application routes |
| `lib/api.js` | Centralized API communication |
| `lib/auth.js` | Authentication state |
| `admin/` | Administrative UI |
| `public/` | Static assets |

## Backend Contract

The frontend communicates with the Laravel API through endpoints including:

```http
POST /api/register
POST /api/login
GET /api/profile
POST /api/logout

GET /api/courses
POST /api/courses
PUT /api/courses/{id}
DELETE /api/courses/{id}

POST /api/courses/{id}/like
POST /api/courses/{id}/comment
```

See the backend repository for the complete API surface and authorization rules.

## Local Development

### Requirements

- Node.js
- npm
- Running Laravel backend

### Installation

```bash
git clone https://github.com/artushhhd/course-platform-frontend.git
cd course-platform-frontend

npm install
```

Create `.env.local`:

```env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
```

Start the development server:

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

### Production Build

```bash
npm run build
npm start
```

## Architecture Notes

The frontend keeps HTTP communication centralized, separates authentication concerns from page components, and relies on the Laravel API for authorization.

The application is intentionally separated from the backend so both parts can be developed and deployed independently.