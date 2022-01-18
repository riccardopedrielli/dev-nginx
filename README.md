# dev-nginx

NGINX service for development and testing purposes.

## Prerequisites

Install [Docker](https://docs.docker.com/engine/install/)
and [Docker Compose](https://docs.docker.com/compose/install/).

The logging driver is set to `local`.  
Follow this guide to configure the docker daemon to use the
[local file logging driver](https://docs.docker.com/config/containers/logging/local/).

## Configuration

To set a custom configuration create a file in `~/.config/docker-dev-tools/dev-nginx/settings.env`
and add the variables to override.

Use `./servicectl.sh info` for the list of available variables and their values.

When setting paths, always use the unix slash `/` even on Windows.

> **Note:** `~` is an alias for the user's home directory.
>
> - Linux: `/home/<username>`
> - macOS: `/Users/<username>`
> - Windows: `C:/Users/<username>`
>
> The `${HOME}` variable is also available but can lead to compatibility issues, especially on Windows.

### Data persistence

By default the persistence directory is set to `~/.local/share/docker-dev-tools/dev-nginx`.

Any custom directory should be set in a path inside the user's home directory.
Setting it outside is not supported and, depending on the host platform, may not work.

There's no need to manually create directory, Docker Compose will take care if it.

## Usage

To manage the service, execute `./servicectl.sh <command>`.

| Command | Description                                                             |
| :------ | :---------------------------------------------------------------------- |
| `up`    | Bring up the service.                                                   |
| `down`  | Bring down the service.                                                 |
| `info`  | Show informations about the service: name, config, status.              |
| `logs`  | Show service's logs, takes the same arguments as `docker compose logs`. |

### Host

On Linux and macOS the services are available at `localhost`.

On Windows the services are available at the virtual machine's ip. Usually `192.168.99.100`,
can be inspected with `docker-machine ip`.

### Default ports

| Type       | Application | Default port |
| :--------- | :---------- | :----------: |
| Web server | `nginx`     |    `8088`    |
