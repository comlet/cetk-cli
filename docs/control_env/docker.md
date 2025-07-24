# Control Environment: Docker (On Premise)
This control environment encapsulates and delegates the execution of [supported executables](index.md#supported-executables) to a [Linux Docker container](#docker-image)
as part of a Docker compose environment.

## System Requirements
--8<-- "snippets/docker_req.md"

--8<-- "snippets/control_env_sys_req.md"

## Environment Variables
[See the common environment variables set.](index.md#within-control-environment)

Additionally, the following environment variables are set:

- `CETK_DOCKER_IMAGE`: The Docker image representing the control environment

## Volumes
During execution, the following local paths are mounted as volumes into the Docker container representing the control environment:

- [`Source Home`](../home_folder/source_home.md)
- [`Output Home`](../home_folder/output_home.md)
- [`Temp Home`](../home_folder/temp_home.md)
- Current working directory

## Configuration
### Mandatory
- `--environment=docker`
- `--docker-image`: Name of the [Docker image](#docker-image) representing the control environment

### Optional
- `--compose-file`: Additional compose files defining additional services
- `--compose-dotenv-file`: Path to a dotenv file passed to Docker compose

??? tip
    See [cetk-cli's global options](../cli/global_options.md) for further details.

## Docker Image
A pre-built Linux Docker image is provided that can be stored locally or within a Docker registry.
This image can also be used as a base image for a project-specific adjustments.

### Docker Compose Service
The service which is part of the Docker compose environment, in which the [supported executables](index.md#supported-executables) are run, is called `embedded_testkit`.

## Security Considerations
For security reasons, the executables within the control environment are run by a non-privileged user that gets the same User and Group ID
than the local user[^1]. Additionally, it is made sure that the files read from and written to the [volumes](#volumes) have the same access control rights than the
local user only.
There is no root/privileged user involved that may leak into the host even when running the Docker engine service as root.

[^1]: On non-posix systems it falls back to a default value since it does not matter
