# Getting Started

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

## Start the Documentation

Build the Docker image and start the container:

```bash
docker compose up -d --build
```

Open the website at [http://localhost:8082](http://localhost:8082).

## Stop the Documentation

```bash
docker compose down
```
