# Hono API with Auth Crash Course

A REST API built with [Hono](https://hono.dev/), Node.js, [Drizzle ORM](https://orm.drizzle.team/), PostgreSQL, and Zod validation.

## Prerequisites
- Node.js (v20+)
- Docker (for running the PostgreSQL database)

## Getting Started

### 1. Environment Variables
Create a `.env` file in the root of the project and add the following variables:

```env
PORT=3000
DB_PASSWORD=postgres
DB_USER=postgres
DB_NAME=hono_api
DB_HOST=localhost
DB_PORT=5433
JWT_SECRET=supersecretjwtkey
```

### 2. Start the Database
Start the PostgreSQL database using Docker Compose:

```bash
docker compose up -d
```

### 3. Install Dependencies
Install the required packages using npm:

```bash
npm install
```

### 4. Database Setup
If using Drizzle ORM, push your schema to the database:
```bash
npx drizzle-kit push
```

### 5. Run the Application
Start the development server:

```bash
npm run dev
```

The API will be available at [http://localhost:3000](http://localhost:3000).

### 6. Generating a secure JWT_SECRET for your .env file
Instead of using "supersecretjwtkey", it's best to use a strong, randomly generated string. You can generate one quickly in your terminal using Node.js:

bash
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
Or using openssl if you have it installed:

bash
openssl rand -hex 32
Copy the output and paste it into your .env file

## Scripts
- `npm run dev` - Starts the development server with hot-reload (`tsx watch`)
- `npm run build` - Builds the project using TypeScript (`tsc`)
- `npm start` - Starts the built production server
