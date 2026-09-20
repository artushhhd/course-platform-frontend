# Course Platform — Frontend

Next.js 16 frontend for a course platform connected to a separate Laravel REST API.

**Backend:** https://github.com/artushhhd/junior-backend-api

## Tech Stack

- Next.js 16.2.7
- React 19.2.4
- JavaScript
- Tailwind CSS 4
- Native Fetch API
- Laravel Sanctum

## Key Features

### Authentication

- Registration, login, logout
- Token persistence
- Protected user flows
- Profile page
- Backend validation errors
- Automatic handling of invalid or expired authentication

### Courses

- Browse courses
- View course details
- Create courses
- Upload course images
- Edit and delete owned courses
- Like / unlike courses
- Add comments

### Administration

The `/admin` area provides:

- Course moderation
- Course approval
- User management
- Account blocking
- Administrative actions

The frontend does not replace backend security. Authorization decisions are made by the Laravel API.

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

The backend URL is configured with an environment variable instead of being hardcoded throughout the application:

```env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
```

## Project Structure

```text
app/
├── page.js
├── login/
├── profile/
├── Course/
├── addCourse/
├── admin/
├── layout.js
└── ClientLayoutHelper.jsx

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

The frontend communicates with the Laravel API using endpoints including:

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

GET /api/admin/...
```

See the backend repository for the complete API and authorization rules.

## Installation

### Requirements

- Node.js
- npm
- Running Laravel backend

### 1. Clone

```bash
git clone https://github.com/artushhhd/junior-frontend-app.git
cd junior-frontend-app
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure the API

Create `.env.local`:

```env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
```

Make sure the Laravel backend is running.

### 4. Start development

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

### 5. Production build

```bash
npm run build
npm start
```

## Project Purpose

This portfolio project demonstrates practical frontend development with Next.js and React:

- App Router
- REST API integration
- Authentication flows
- Protected UI
- Form handling
- Error handling
- Role-aware interfaces
- Centralized HTTP communication
- Environment-based configuration

The frontend and backend are intentionally separated so they can be developed and deployed independently.
