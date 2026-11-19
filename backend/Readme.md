# Backend

The backend is an Express 5 REST API with a Socket.IO server, Sequelize/MySQL models, JWT authentication, Multer uploads, and Swagger documentation.

## Setup

```powershell
npm install
npm run dev
```

Create a `.env` file in this directory with the following variables:

```env
PORT=5000
DB_NAME=social_app_db
DB_HOST=127.0.0.1
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_mysql_password
JWT_SECRET=use_a_long_random_secret
```

The server starts at `http://localhost:5000`. Swagger documentation is available at `http://localhost:5000/api-docs`.

## Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start with Nodemon |
| `npm start` | Start the server normally |
| `npm test` | Run Jest and Supertest suites |

## Source Layout

- `src/app.js`: Express middleware and route registration
- `src/server.js`: HTTP server startup and database connection
- `src/config/`: Database configuration
- `src/controllers/`: API request handlers
- `src/middlewares/`: JWT auth, uploads, logging, and errors
- `src/models/`: Sequelize models and associations
- `src/routes/`: REST and Swagger route declarations
- `src/services/`: Shared backend services
- `src/socket/`: Real-time message handling
- `src/tests/`: Backend test suites
- `uploads/`: Uploaded profile and post images

The Sequelize configuration uses `sequelize.sync({ alter: true })`, so model changes are synchronized into the MySQL schema at startup.