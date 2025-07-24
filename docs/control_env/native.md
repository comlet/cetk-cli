# Control Environment: Native (On Premise)
This control environment has the least form of encapsulation and assumes that the [supported executables](index.md#supported-executables) are installed and
available within the system's or user's path.

This can be anything from installing them globally, within a active Python virtualenv, an active Conda environment,
within a Virtual Machine, even a Docker image (in which [cetk-cli](../cli/index.md) is also installed to), etc.

Alternatively, the Python interpreter that has the [supported executables](index.md#supported-executables) installed, can be selected manually by
setting `CETK_PYTHON` environment variable.

## System Requirements
--8<-- "snippets/control_env_sys_req.md"

## Environment Variables
[See the common environment variables set.](index.md#within-control-environment)

## Configuration
- `--environment=native` (default value)

??? tip
    See [cetk-cli's global options](../cli/global_options.md) for further details.

## Option: Start a Docker Compose Environment
If needed, the native control environment supports starting and stopping a Docker compose environment automatically that test suites
may utilize.

--8<-- "snippets/docker_req.md"

??? info "Difference to the Docker compose environment started by docker control environment"
    The difference is that the test execution is not part of the Docker compose network (since executed natively).
    Whereas the test execution with the Docker control environment is part of the Docker compose network as a dedicated service.

For configuration, see the [Docker control environment configuration section](docker.md#configuration).
