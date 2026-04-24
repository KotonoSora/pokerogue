# Production Docker Compose Usage

This project supports building and running the production Vite build using Docker Compose and Node.js + serve.

## Quick Start

1. Ensure your `.env.production` contains all required `VITE_` variables for your build.
2. Build and run the production container:

```sh
cd docker
# Build and run
docker compose -f docker-compose.prod.yml up --build
```

3. Open http://localhost:8000 to view the app.

## How it works
- The multi-stage Dockerfile builds the app with pnpm and Vite, then serves the static files from `dist/` using `serve` on port 8000.
- Only production files are included in the final image.
- Environment variables must be set at build time (see `.env.production`).

## Files
- `docker/Dockerfile.prod` — Multi-stage Dockerfile for production build and serve
- `docker/docker-compose.prod.yml` — Compose file for production server
- `.env.production` — Vite build-time environment variables

## Notes
- No runtime environment variable injection is supported (Vite static build).
- For custom domains or HTTPS, extend the Compose or Dockerfile as needed.
