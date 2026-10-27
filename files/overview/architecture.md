# Architecture

This repository provides a reusable documentation environment based on Zensical, Docker, and Nginx.

## Components

- **Zensical**: Generates the static documentation website from Markdown files.
- **Docker**: Builds the documentation image using the configured tool versions.
- **Nginx**: Serves the generated static website over HTTP.
- **GitHub Actions**: Validates the documentation build and Docker image, and optionally deploys the website to GitHub Pages.
- **`.env`**: Centralizes the Python, Nginx, and Zensical versions used by the local Docker build and CI workflow.
- **Docker Compose**: Defines the local service configuration and passes the configured versions to the Docker build.

## Build Process

1. Docker uses the repository root as the build context.
2. The Dockerfile copies the documentation sources into the build environment.
3. The Python build stage installs the configured Zensical version.
4. Zensical generates the static website.
5. The generated website is copied into the final Nginx image.
6. Nginx serves the generated files on port `80`, mapped to port `8082` on the host.

The final container only contains Nginx and the generated website, keeping the runtime image lightweight.

## Continuous Integration

The reusable workflow in `.github/workflows/docs.yml` performs the following checks:

1. Loads the tool versions from `.env`.
2. Builds the documentation with Zensical.
3. Verifies that the generated `index.html` exists.
4. Builds the Docker image using the configured versions.
5. Starts the container and checks its HTTP response.
6. Deploys the website to GitHub Pages if deployment is enabled.

The workflow uses `workflow_call`, allowing another workflow to invoke it.

Deployment is disabled by default and must be explicitly enabled by the calling workflow.