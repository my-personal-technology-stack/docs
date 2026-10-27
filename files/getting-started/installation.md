# Installation

This guide explains how to run the documentation website locally.

## Requirements

Make sure the following tools are installed:

- Git
- Docker
- Docker Compose

## Clone the Repository

```bash
git clone <repository-url>
cd Docs
```

Replace `<repository-url>` with the repository URL.

## Configure Tool Versions

The `.env` file at the repository root defines the versions used by the Docker build.

Example:

```dotenv
PYTHON_VERSION=3.12
NGINX_VERSION=1.27-alpine
ZENSICAL_VERSION=0.0.73
```

These values are automatically loaded by Docker Compose and passed to the Docker build through `build.args`.

Keep the values synchronized with the default arguments defined in `docker/Dockerfile`.

## Start the Documentation

From the repository root, run:

```bash
docker compose up -d --build
```

Open the website at [http://localhost:8082](http://localhost:8082).

## Check the Container

```bash
docker compose ps
```

To inspect the container logs:

```bash
docker compose logs -f
```

## Stop the Documentation

```bash
docker compose down
```