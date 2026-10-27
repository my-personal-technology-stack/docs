# Documentation

Welcome to the **Docs** repository.

This repository provides a reusable documentation structure based on [Zensical](https://zensical.org/), Docker, and Nginx. It can be cloned and adapted across projects.

## Documentation

### Overview

Learn how the documentation environment works and how its components interact.

- [Architecture](overview/architecture.md) — Understand the build process and the role of each component.

### Getting Started

Set up and run the documentation locally.

- [Installation](getting-started/installation.md) — Clone the repository and start the documentation with Docker Compose.

### Maintenance

Learn how to maintain and update the documentation.

- [Updates and Best Practices](maintenance/updates.md) — Update tool versions, rebuild the website, and maintain the documentation environment.

## Quick Start

Start the documentation locally from the repository root:

```bash
docker compose up -d --build
```

Open the website at [http://localhost:8082](http://localhost:8082).

To stop the environment:

```bash
docker compose down
```

## Continuous Integration

The repository includes a reusable GitHub Actions workflow that can be called by another project's CI workflow.

It builds and validates the documentation, builds the Docker image, and checks that the website responds over HTTP. It can also deploy the documentation to GitHub Pages when explicitly enabled by the calling workflow.

## Technology Stack

- [Zensical](https://zensical.org/) — Static documentation generator
- [Docker](https://www.docker.com/) — Build and containerization
- [Nginx](https://nginx.org/) — Static website hosting
- [GitHub Actions](https://github.com/features/actions) — Continuous integration and deployment