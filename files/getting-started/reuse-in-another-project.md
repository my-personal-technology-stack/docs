# Reuse the Documentation Template

This repository provides a reusable documentation structure based on Zensical, Docker, Nginx, and GitHub Actions.

You can use it as a starting point for another project and customize the documentation without rebuilding the entire setup.

## 1. Create a Project from the Template

Create a new repository using the GitHub template feature, if enabled, or copy the contents of this repository into your project.

The new repository should retain the following structure:

```text
your-project/
├── .env
├── .github/
│   └── workflows/
│       └── docs.yml
├── docker/
│   └── Dockerfile
├── docker-compose.yml
└── files/
    ├── zensical.toml
    ├── index.md
    ├── overview/
    ├── getting-started/
    └── maintenance/
```

The copy is independent of the original repository. Updates to the original template are not automatically applied to existing projects.

## 2. Customize the Documentation

Edit the Markdown files in `files/` to describe your project.

For example:

- `files/index.md` — Project documentation home page
- `files/overview/` — Architecture and technical overview
- `files/getting-started/` — Installation and setup instructions
- `files/maintenance/` — Maintenance procedures and best practices

Update the navigation in `files/zensical.toml` to match the pages you keep or add.

## 3. Build the Documentation Locally

From the project root, run:

```bash
docker compose up -d --build
```

Open [http://localhost:8082](http://localhost:8082) to check the generated website.

Stop the environment with:

```bash
docker compose down
```

## 4. Run the Workflow Locally in the New Repository

The copied `.github/workflows/docs.yml` runs automatically when changes are pushed to the `main` branch.

It builds and validates the documentation, builds the Docker image, checks the HTTP response, and deploys the website to GitHub Pages.

To enable deployment, configure GitHub Pages to use GitHub Actions in the repository settings.

## 5. Reuse the Central Workflow Instead

Instead of maintaining a copy of the CI workflow, a project can call the workflow from this repository.

Create or update a workflow in the consuming project, for example `.github/workflows/ci.yml`:

```yaml
name: Project CI

on:
  push:
    branches:
      - main

permissions:
  contents: read

jobs:
  docs:
    uses: my-personal-technology-stack/docs/.github/workflows/docs.yml@v1.1.0
    with:
      deploy_pages: true
    permissions:
      contents: read
      pages: write
      id-token: write
```

Replace `my-personal-technology-stack` with the actual GitHub owner if necessary.

The consuming repository must still contain the files expected by the workflow, including `.env`, `files/`, and `docker/Dockerfile`, because the workflow checks out and builds the calling repository.

The example above runs the documentation workflow on pushes to `main`. The calling workflow determines when the reusable workflow is invoked.

## 6. Choose the Appropriate Approach

- **Copied workflow:** use the template's own `docs.yml`. The project can modify its CI independently.
- **Central reusable workflow:** call the workflow at a versioned reference such as `@v1.1.0`. This reduces duplicated CI configuration, but updates to the central workflow may affect consuming projects when they change the referenced version.

For GitHub Pages deployment from a consuming project, enable Pages for that repository and grant the required `pages: write` and `id-token: write` permissions.

## Best Practices

- Keep project-specific content in Markdown files.
- Pin the central workflow to a stable version tag.
- Test documentation changes locally before pushing.
- Do not store secrets in the version-controlled `.env` file.
- Update the reusable workflow reference deliberately when adopting a new version.