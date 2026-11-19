# Facebook-Like Social Application

A full-stack social networking application with authentication, profiles, posts, likes, comments, friend requests, direct messages, notifications, reporting, and admin moderation.

## Tech Stack

### Frontend

- React 19
- Vite 8
- React Router DOM 7
- Tailwind CSS 4
- Axios
- Socket.IO Client
- Vitest and React Testing Library

### Backend

- Node.js ES modules
- Express 5
- MySQL
- Sequelize ORM
- JSON Web Tokens
- bcrypt/bcryptjs
- Socket.IO
- Multer
- Swagger UI
- Jest and Supertest

## Features

- User registration and login with JWT authentication
- Profile details and profile-image uploads
- Global and friends-only feeds
- Text posts with optional image uploads
- Likes, comments, saved posts, and post deletion
- Friend suggestions, requests, acceptance, rejection, and removal
- Real-time direct messaging and online socket registration
- User blocking and chat-history blocking checks
- Notifications and real-time alerts
- Community reports
- Admin dashboard for users and reports
- Account banning and report-status management
- Swagger API documentation

## Project Structure

```text
facebook-like-app/
|-- backend/
|   |-- src/
|   |   |-- config/          # Sequelize/MySQL configuration
|   |   |-- controllers/     # Request handlers
|   |   |-- middlewares/     # Authentication, uploads, logging, errors
|   |   |-- models/          # Sequelize models and relationships
|   |   |-- routes/          # REST API route definitions
|   |   |-- services/        # Reusable business logic
|   |   |-- socket/          # Socket.IO server setup
|   |   |-- tests/          # Backend Jest/Supertest tests
|   |   |-- utils/           # Helpers and token utilities
|   |   |-- app.js           # Express application setup
|   |   `-- server.js        # HTTP server and database startup
|   `-- uploads/             # Uploaded profile and post images
`-- frontend/
    |-- src/
    |   |-- api/              # Axios configuration
    |   |-- context/          # Socket context
    |   |-- features/         # Auth, posts, follows, messages, reports, admin
    |   |-- routes/           # Public, protected, and admin routing
    |   `-- tests/            # Vitest and React Testing Library tests
    |-- index.html
    `-- vite.config.js
```

## Prerequisites

- Node.js 18 or newer
- npm
- MySQL 8 or a compatible MySQL server

## Backend Setup

1. Create a MySQL database:

```sql
CREATE DATABASE social_app_db;
```

2. Enter the backend directory:

```powershell
cd backend
```

3. Install dependencies:

```powershell
npm install
```

4. Create or update `backend/.env` with local values:

```env
PORT=5000
DB_NAME=social_app_db
DB_HOST=127.0.0.1
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_mysql_password
JWT_SECRET=use_a_long_random_secret
NODE_ENV=development
```

Do not commit real database passwords or JWT secrets. Replace the example values with credentials for your local environment.

5. Start the backend:

```powershell
npm run dev
```

The API runs at `http://localhost:5000`.

Sequelize authenticates the database and synchronizes the schema with `alter: true` during startup.

## Frontend Setup

1. Open a second terminal and enter the frontend directory:

```powershell
cd frontend
```

2. Install dependencies:

```powershell
npm install
```

3. Create or update `frontend/.env`:

```env
VITE_API_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
```

4. Start the Vite development server:

```powershell
npm run dev
```

The frontend runs at `http://localhost:5173`.

The Axios client uses `VITE_API_URL`. The socket context uses the local Socket.IO server URL during development.

## Running the Application

Run both processes in separate terminals:

```powershell
# Terminal 1
cd backend
npm run dev

# Terminal 2
cd frontend
npm run dev
```

Open `http://localhost:5173` in a browser. The backend must be available at `http://localhost:5000` for REST requests and Socket.IO connections.

## API Documentation

With the backend running, open:

```text
http://localhost:5000/api-docs
```

Swagger is generated from route annotations under `backend/src/routes`.

## Main API Areas

| Area | Base route | Main operations |
| --- | --- | --- |
| Authentication | `/api/auth` | Register and login |
| Profile | `/api/profile` | View and update profile |
| Posts | `/api/posts` | Create, delete, save, global feed, friends feed |
| Likes | `/api/likes` | Toggle post likes |
| Comments | `/api/comments` | Add and manage comments |
| Notifications | `/api/notifications` | Retrieve notifications and alerts |
| Follows | `/api/follows` | Suggestions, requests, friends |
| Messages | `/api/messages` | Chat history and user blocking |
| Reports | `/api/reports` | Submit community reports |
| Admin | `/api/admin` | Manage users and reports |

Protected endpoints accept a bearer token:

```text
Authorization: Bearer <JWT_TOKEN>
```

## Testing

Run backend tests:

```powershell
cd backend
npm test
```

Run frontend tests once:

```powershell
cd frontend
npm run test:run
```

Start frontend tests in watch mode:

```powershell
cd frontend
npm test
```

Run the frontend lint check:

```powershell
cd frontend
npm run lint
```

Create a production frontend build:

```powershell
cd frontend
npm run build
```

## Uploaded Files

Multer stores uploaded files in `backend/uploads`. The backend serves this directory at:

```text
http://localhost:5000/uploads/<filename>
```

The frontend currently also references media through the local backend origin.
