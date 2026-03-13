# Docker Setup for URL Shortener

## Quick Start

### Using Docker Compose (Recommended)

1. Build and start the services:
```bash
docker-compose up --build
```

2. Access the application at `http://localhost:8080`

### Using Dockerfile Only

1. Build the image:
```bash
docker build -t url-shortener .
```

2. Run the container:
```bash
docker run -p 8080:8080 --env-file url-shortener/.env url-shortener
```

## Configuration

The project uses environment variables from `url-shortener/.env`. For local Docker development with PostgreSQL:

- Update `DB_HOST` to `db` in your `.env` file when using docker-compose
- Or use the provided `.env.docker` file

## Database

The docker-compose setup includes a PostgreSQL database. Migrations run automatically on startup.

To run migrations manually:
```bash
docker-compose exec web python manage.py migrate
```

## Stopping Services

```bash
docker-compose down
```

To remove volumes as well:
```bash
docker-compose down -v
```
