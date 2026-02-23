# OpenSamguk Deploy

Deployment-only repository for OpenSamguk.

Contains only runtime deployment artifacts:
- `docker-compose.yml`
- `nginx/nginx.conf`
- `.env.example`

## Quick Start

1) Copy env file
```bash
cp .env.example .env
```

2) Edit secrets in `.env` (at least `DB_PASSWORD`)

3) Pull and run
```bash
docker compose pull
docker compose up -d
```

## Update to latest images
```bash
docker compose pull
docker compose up -d
```

## Pin a specific version (commit SHA)
```bash
TAG=<commit-sha> docker compose up -d
```
