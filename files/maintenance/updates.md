# Maintenance

## Update the Repository

Pull the latest changes from the current Git branch:

```bash
git pull
```

## Rebuild the Website

Rebuild the image and restart the container to apply the changes:

```bash
docker compose up -d --build
```

## Update Documentation Content

1. Add or edit Markdown files.
2. Update `zensical.toml` if the navigation changes.
3. Rebuild the Docker image.
4. Verify the website locally.

## Best Practices

- Keep documentation clear and concise.
- Use consistent Markdown formatting.
- Keep navigation up to date.
- Test changes locally before sharing them.
