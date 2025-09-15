# cls.github.io

A Jekyll-powered GitHub Pages site that runs entirely in Docker for consistent development environments.

## Prerequisites

- Docker
- Make

## Quick Start

```bash
# Build and serve the site locally
make serve
```

Visit `http://localhost:4000` to view your site.

## Available Make Commands

### `make build`
Builds the Docker image with all Jekyll dependencies.

### `make serve`
Builds the Docker image (if needed) and starts the Jekyll development server. The site will be available at `http://localhost:4000` with live reload enabled.

### `make inter`
Starts an interactive bash session inside the Docker container for debugging or manual operations.

### `make trace`
Runs the Jekyll server with trace output enabled for debugging build issues.

### `make clean`
Removes Docker containers and volumes associated with the Jekyll bundle cache. Use this if you encounter dependency issues.

### `make rebuild`
Performs a complete cleanup and rebuild: runs `clean`, `build`, and `serve` in sequence.

## Configuration

The site uses two configuration files:
- `_config.yml` - Main Jekyll configuration
- `_config_local.yml` - Local development overrides

## Docker Setup

The project uses a Ruby 3.1-based Docker image with:
- Jekyll and required gems
- Node.js for asset compilation
- Bundler 2.4.19 for dependency management
- Persistent gem cache via Docker volume

## Development Workflow

1. Make changes to your Jekyll site files
2. Run `make serve` if not already running
3. View changes at `http://localhost:4000`
4. Changes are automatically reloaded thanks to Jekyll's built-in live reload

## Troubleshooting

If you encounter issues:
1. Try `make clean` followed by `make serve`
2. Use `make trace` to see detailed error messages
3. Use `make inter` to debug inside the container