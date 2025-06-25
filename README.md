# GitHub CLI Docker Wrapper

This project provides a Dockerized environment for the [GitHub CLI (`gh`)](https://cli.github.com/), allowing you to use the CLI tool in a consistent, isolated container. It includes scripts for building the Docker image and running the CLI with your local configuration and authentication.

## Features

- Runs the latest GitHub CLI in an Ubuntu 22.04 container.
- Mounts your local configuration, authentication, and SSH keys for seamless use.
- Simple build and run scripts.
- No need to install `gh` or dependencies on your host system.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on your system
- Bash shell

## Installation

Clone this repository to your local machine:

```sh
git clone https://github.com/mbuyco/docker-gh.git \
    && cd docker-gh \
    && ./bin/build
```

Link bin directory to your PATH for easy access:

```sh
sudo ln -s "$(pwd)/bin" /usr/local/bin/docker-gh"
```

Restart your terminal and run:

```sh
docker-gh --version
```

This script mounts your current directory as the working directory inside the container, as well as your GitHub CLI config, authentication, and SSH keys.

## File Overview

- `Dockerfile`: Defines the Docker image with the GitHub CLI installed.
- `bin/build`: Script to build the Docker image.
- `bin/docker-gh`: Wrapper script to run `gh` inside the container.

## Notes

- Your GitHub CLI configuration and authentication are shared with the container via volume mounts.
- The container runs as root for compatibility with mounted config files.
- The default entrypoint is `gh`, so you can pass any `gh` command and arguments.

## License

MIT License (c) 2025 mbuyco
