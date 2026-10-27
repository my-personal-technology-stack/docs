# Updates and Best Practices

This page describes how to update the repository and maintain the documentation environment.

## Update the Repository

Pull the latest changes from the current Git branch:

```bash
git pull
```

## Update Tool Versions

The `.env` file centralizes the versions used by the Docker build and GitHub Actions workflow.

When updating a tool version:

1. Modify the corresponding value in `.env`.
2. Update the matching default argument in `docker/Dockerfile`.
3. Rebuild the Docker image.
4. Verify the website locally.
5. Commit and push the changes.

The `.env` file contains tool versions only. Do not store secrets in a version-controlled file.

## Rebuild the Website

From the repository root, run:

```bash
docker compose up -d --build
```

To stop the environment:

```bash
docker compose down
```

## Continuous Integration

The reusable workflow `.github/workflows/docs.yml` validates the documentation build and Docker image.

It can be called from another workflow using `workflow_call`. The calling workflow controls whether GitHub Pages deployment is enabled through the `deploy_pages` input.

Deployment should only be enabled for the intended stable branch or release process.

## Best Practices

- Keep documentation clear and concise.
- Use consistent Markdown formatting.
- Keep navigation up to date in `zensical.toml`.
- Pin tool versions for reproducible builds.
- Keep `.env` values and Dockerfile defaults synchronized.
- Test changes locally before sharing them.
- Never store secrets in a version-controlled `.env` file.
- Use versioned Git tags when publishing stable releases.