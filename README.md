# ESKAPE Analysis Application

A web application for analyzing microscopic urine sample images to detect ESKAPE category bacteria.

#Created By:
Siddharth Sandeep - 22070122210
Pranavi Singh - 22070122211
Shreyas Tambe - 22070122221
Vedant Ambadkar - 22070122247

## Prerequisites

- Node.js (v18 or higher)
- MongoDB installed locally or MongoDB Atlas account
- Git

## Installation Steps

1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-name>
```

## PathoScanAI — ESKAPE Analysis Application

PathoScanAI is a full-stack web application for analyzing microscopic urine sample images and classifying possible ESKAPE-category bacteria using TensorFlow.js and image processing.

This repository contains an Express backend (server/) and a Vite + React frontend (client/) wired together so the single `npm run dev` command runs the server and serves the client in development.

## Key features

- Upload and analyze microscopic images
- View results and confidence scores
- Persist analysis history

## Tech stack

- Frontend: React + Vite, TailwindCSS, shadcn/ui
- Backend: Node.js + Express
- Database: MongoDB (Mongoose)

## Prerequisites

- Node.js v18+ (tested with v18+)
- npm (or pnpm/yarn) — commands below use npm
- MongoDB (local) or MongoDB Atlas connection string
- On macOS, installing `sharp` may require libvips: `brew install vips`

## Environment

Create a `.env` file in the project root. The server requires at least:

```
MONGODB_URI=mongodb://localhost:27017/your_db_name
PORT=8080       # optional, defaults to 8080
```

Adjust values for production as needed.

## Quickstart — local development

1. Install dependencies

```bash
npm install
```

2. Start dev server (backend + Vite-powered frontend)

```bash
npm run dev
```

Open http://localhost:8080 in your browser. The server listens on PORT (default 8080). The dev server uses Vite middleware, so frontend HMR works while the Express backend is running.

## Production build

1. Build the client and bundle the server

```bash
npm run build
```

This runs Vite build for the client and uses esbuild to bundle `server/index.ts` into `dist/`.

2. Start the production server

```bash
npm start
```

The server will serve the built client from the `dist`/public folder.

## Docker

This repository includes a `Dockerfile` and `docker-compose.yml` for containerized runs. Typical steps:

```bash
docker-compose up --build
```

Check the `docker-compose.yml` for service names and ports.

## Useful scripts

- `npm run dev` — start Express server with Vite middleware (development)
- `npm run build` — build client (Vite) and bundle server (esbuild)
- `npm start` — run production server (`NODE_ENV=production node dist/index.js`)
- `npm run check` — run TypeScript compiler checks
- `npm run db:push` — run drizzle-kit push (if using drizzle migrations)


## API (examples)

The backend defines routes under `/api` (see `server/routes.ts`). Typical endpoints:

- `GET /api/health` — health/status
- `POST /api/analyze` — upload + analyze image
- `GET /api/analyses` — list previous analyses
- `GET /api/analysis/:id` — get one analysis result

Refer to `server/routes.ts` for the most up-to-date endpoints and payload shapes.
