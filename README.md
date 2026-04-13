NAME: Dramane Traore
UID: 24BCY70270


EXP 8B: Banking API Implementation Guide (with Winston Logging)

Objective:To build a secure and highly observable Banking API from scratch.

Project Architecture Overview
This project is built using Node.js, Express, and MongoDB. It features:

Authentication: JWT-based session management with argon2 hashing.
Observability: Production-grade logging using Winston.
Security: Granular rate-limiting using rate-limiter-flexible.
Database: Mongoose for modeling and validation.

🛠️ Step-by-Step Implementation
Step 1: Project Initialization
       Initialize the project:
        pnpm init
       Install dependencies:
        pnpm add express mongoose jsonwebtoken argon2 cors dotenv winston rate-limiter-flexible http-errors http-status-codes
     Add a development script in package.json:
"scripts": {
  "dev": "nodemon index.js"
}
Step 2: Environment Setup
Create a .env file for your configuration:

MONGO_URI=your_mongodb_uri
PORT=3000
LOG_LEVEL=info
JWT_SECRET=your_secret
JWT_REFRESH_SECRET=your_refresh_secret
JWT_EXPIRES_IN=5m
Step 3: Global Winston Configuration (config/logger.js)
        We use Winston to centralize all application logs.
        import winston from "winston";

Step 4: Request Logging Middleware (middleware/logger.middleware.js)
This middleware captures every incoming request and logs its duration.

Step 5: Master Error Handling (middleware/error.middleware.js)
Centralizing error logging ensures that stack traces are always captured in your error.log.

Step 6: Database Connectivity (config/db.js)
Ensure your database connection attempts are also logged via Winston.


EXPERIMENT FOLDER STRUCTURE
24bcy70270-8b-dramane-traore
.
├── config/
│   ├── db.js
│   └── logger.js
├── controllers/
│   └── auth.controller.js
├── models/
│   └── user.model.js
├── middleware/
│   ├── error.middleware.js
│   ├── logger.middleware.js
│   └── ratelimit.middleware.js
├── routes/
│   └── auth.routes.js
├── logs/ (Ignored by Git)
├── .env
├── .gitignore
├── index.js
└── package.json

Running the Application
Prepare Logs: Winston will automatically create the logs/ folder if it doesn't exist.
Start Dev Server:
pnpm dev
Check Output:
Success logs will appear in combined.log.

screenshots: <img width="865" height="879" alt="image" src="https://github.com/user-attachments/assets/655f1f2c-c532-4c61-9525-0bcdca03be0f" />
<img width="873" height="903" alt="image" src="https://github.com/user-attachments/assets/5745e844-89f7-4b72-ba42-a6fbc221a7e1" />


