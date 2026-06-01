# Hono API with Auth

[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Hono](https://img.shields.io/badge/Hono-E36002?style=for-the-badge&logo=hono&logoColor=white)](https://hono.dev/)
[![Drizzle](https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=for-the-badge&logo=drizzle&logoColor=black)](https://orm.drizzle.team/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)

A robust, blazing-fast REST API built with Node.js and Hono, featuring JWT authentication, seamless database integration with Drizzle ORM, and comprehensive data validation via Zod.

## ✨ Features

- **Blazing Fast**: Powered by [Hono](https://hono.dev/), a small, simple, and ultrafast web framework.
- **Robust Authentication**: Secure JWT-based authentication workflow.
- **Type-safe Database Operations**: Utilizing [Drizzle ORM](https://orm.drizzle.team/) with PostgreSQL.
- **Schema Validation**: First-class data validation using [Zod](https://zod.dev/).
- **Containerized Database**: Easy local setup with Docker Compose.
- **Developer Experience**: Hot-reloading built-in with `tsx`.

## 🛠️ Tech Stack

- **Framework**: Hono, Node.js
- **Language**: TypeScript
- **Database**: PostgreSQL
- **ORM**: Drizzle ORM
- **Validation**: Zod
- **Tooling**: Docker, tsx, dotenv

## 🚀 Getting Started

Follow these steps to set up the project locally.

### Prerequisites

Ensure you have the following installed on your machine:
- **Node.js** (v20 or higher)
- **Docker** and **Docker Compose** (for running the PostgreSQL database)

### 1. Clone & Install

Clone the repository and install the dependencies:

```bash
npm install
```

### 2. Environment Configuration

Create a `.env` file in the root of the project and populate it with the required environment variables:

```env
PORT=3000
DB_PASSWORD=postgres
DB_USER=postgres
DB_NAME=hono_api
DB_HOST=localhost
DB_PORT=5433
JWT_SECRET=supersecretjwtkey
```

> **Security Tip**: Always use a strong, cryptographically secure `JWT_SECRET` in production. You can generate one using:
> ```bash
> node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
> ```
> Or via OpenSSL:
> ```bash
> openssl rand -hex 32
> ```

### 3. Start the Database

Spin up the PostgreSQL database using Docker:

```bash
docker compose up -d
```

### 4. Database Schema Setup

Push the Drizzle ORM schema to synchronize your database:

```bash
npx drizzle-kit push
```

### 5. Run the Application

Start the development server with hot-reload enabled:

```bash
npm run dev
```

The API will now be running and accessible at [http://localhost:3000](http://localhost:3000).

## 📜 Available Scripts

- `npm run dev` - Starts the development server with hot-reload (`tsx watch`).
- `npm run build` - Compiles the project using TypeScript (`tsc`).
- `npm start` - Starts the built production server from the `dist` directory.

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
