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

- [Updates and Best Practices](maintenance/updates.md) — Pull changes, rebuild the website, and keep documentation up to date.

## Quick Start

Start the documentation locally with:

```bash
docker compose up -d --build
```

Then open [http://localhost:8082](http://localhost:8082).

## Technology Stack

- [Zensical](https://zensical.org/) — Static documentation generator
- [Docker](https://www.docker.com/) — Build and containerization
- [Nginx](https://nginx.org/) — Static website hosting
