# camply-compose

Docker configuration for running the [camply](https://github.com/juftin/camply) service.

## Usage

Provide a configuration file and run `docker compose up`.

### systemd

The following systemd configuration can be used to run the service:

```toml
[Unit]
Description="Always-on configuration for the camply service."
Requires="docker.service"

[Service]
User="ctrombley"
Type="forking"
WorkingDirectory="/home/ctrombley/src/github.com/ctrombley/camply-compose"
ExecStart="/bin/bash -c 'docker compose up --detach'"
ExecStop="/bin/bash -c 'docker compose stop'"

[Install]
WantedBy="multi-user.target"
```

## Configuration

Provide a `files/.camply` to configure the service.

### Pushover notifications

For Pushover notifications:

```sh
PUSHOVER_PUSH_USER="..."
PUSHOVER_PUSH_TOKEN="..."
```

### Additional options

[Additional options](https://github.com/juftin/camply/blob/main/docs/examples/example.camply) are available.
