# Frontend

This directory contains the React and Vite frontend for the Facebook-like social application.

## Setup

```powershell
npm install
npm run dev
```

The development server runs at `http://localhost:5173`.

Create a `.env` file with:

```env
VITE_API_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
```

## Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start Vite with hot reload |
| `npm run build` | Create a production build |
| `npm run preview` | Preview the production build |
| `npm run lint` | Run ESLint |
| `npm test` | Run Vitest in watch mode |
| `npm run test:run` | Run Vitest once |

## Source Layout

- `src/api/`: Axios client configuration
- `src/context/`: Socket.IO provider
- `src/features/auth/`: Login, signup, and authentication state
- `src/features/dashboard/`: Main dashboard and notifications
- `src/features/posts/`: Post creation, feeds, comments, likes, and saves
- `src/features/follows/`: Suggestions and friend management
- `src/features/messages/`: Chat and blocking UI
- `src/features/profile/`: Profile UI
- `src/features/reports/`: Community report modal
- `src/features/admin/`: Admin dashboard
- `src/routes/`: Public, protected, and admin route guards
- `src/tests/`: Vitest and React Testing Library suites
