# panduza-user-guide

Panduza Dev Zone Documentation !

## Local Tests

```bash
# Run "hugo server"
docker compose up

# Build site
docker compose run --rm hugo ""
# Build site with flags
docker compose run --rm hugo --gc --minify --cleanDestinationDir

# Run a command of Hugo
docker compose run --rm hugo env
```

## Work on theme

Clone theme in "themes" directory, then uncomment the remplacement line in the hugo.toml

`Warning !` You have to clear go.mod and go.sum to avoid cache issue on the version of theme used.
