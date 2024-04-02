# SQLite3

## Usage

```console
docker run --rm \
    -v some_volume:/data \
    -v $(pwd):/backup \
    ghcr.io/hkcomori/sqlite3:latest \
    /data/path/to/db.sqlite ".backup /backup/db.sqlite"
```

## Supported tags and respective `Dockerfile` links

- [latest](Dockerfile)
