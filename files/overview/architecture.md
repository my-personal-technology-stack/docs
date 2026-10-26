# Architecture

## Overview

This repository provides a reusable documentation structure based on Zensical.

It can be cloned and adapted across projects to maintain consistent documentation standards.

## Components

- **Zensical**: Generates the static documentation website from Markdown files.
- **Docker**: Builds and runs the documentation environment.
- **Nginx**: Serves the generated website over HTTP.

## Build Process

1. Docker copies the documentation sources into the build environment.
2. Zensical generates the static website.
3. Nginx serves the generated files.

The final container only contains Nginx and the generated website, keeping the runtime lightweight.
