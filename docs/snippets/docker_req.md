A [Docker engine](https://docs.docker.com/engine/){target="_blank"}[^20] and [Compose v2 cli-plugin](https://docs.docker.com/compose/){target="_blank"}[^21] are expected to be installed and usable by the current user.
This can be achieved by using [Docker Desktop](https://docs.docker.com/desktop/){target="_blank"}, [Ranger Desktop](https://rancherdesktop.io/){target="_blank"}, installing the Docker engine natively, using [Podman](https://podman.io/){target="_blank"}[^22] etc.

[^20]: Tested with version 20.10.6 onwards
[^21]: Tested with version 2.6.0 onwards
[^22]: Make sure to configure the `compose-executable-name` CLI option to `podman`