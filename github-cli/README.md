# GitHub-CLI

## Usage

```console
docker run --rm \
    -e GH_TOKEN=<YOUR_GITHUB_TOKEN> \
    ghcr.io/hkcomori/github-cli:latest \
    <command> <subcommand> [flags]
```

## Supported tags and respective `Dockerfile` links

- [latest](Dockerfile)

- [slim](Dockerfile-slim)
    Some commands depend on git are not available.
