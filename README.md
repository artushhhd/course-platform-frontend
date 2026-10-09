# Course Platform — Frontend

Next.js App Router frontend for the [Course Platform Laravel API](https://github.com/artushhhd/course-platform-backend).

## Features

- React 19 and JavaScript
- Centralized API client in `lib/api.js`
- Authentication flows and token handling
- Course browsing and management
- Image upload integration
- Likes and comments
- Role-aware administration UI
- API validation and error handling

## Technology

Next.js 16 · React 19 · JavaScript · Tailwind CSS 4 · Fetch API

## API Configuration

Create `.env.local` in the frontend root:

```env
NEXT_PUBLIC_API_URL=http://127.0.0.1:8000/api
```

This value must match the base URL expected by `lib/api.js`. If your local API uses a different host or prefix, update the variable accordingly and restart the development server.

The API client centralizes HTTP requests, bearer tokens, JSON and FormData requests, HTTP errors, 401 handling, token cleanup, and media URLs. The Laravel API remains the source of truth for authorization.

## Run Locally

Requirements: Node.js and npm, plus a running backend API.

```bash
git clone https://github.com/artushhhd/course-platform-frontend.git
cd course-platform-frontend
npm install
npm run dev
```

Open the local URL printed by Next.js, usually `http://localhost:3000`.

## Production Build

```bash
npm run build
npm start
```

See the [backend README](https://github.com/artushhhd/course-platform-backend) for API setup.
