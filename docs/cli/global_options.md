# Global Options
Global options can be used before and for every sub-command but may not be processed by every [control environment](../control_env/index.md).

??? example
    ````shell
    cetk [global option] [sub-command] ...
    ````

## Options

### `--help` / `-h`
Show help/usage details and exit.

- Default: None
- Supported control environment(s): All
- Environment variable(s): None

### `--version`
Show `cetk-cli`'s version and exit.

- Default: None
- Supported control environment(s): All
- Environment variable(s): None

---

### `--project-name` (str)
Set a project name used for Docker compose environment and its network.

- Default: `cetk`
- Supported control environment(s): Native, Docker
- Environment variable(s): `CETK_PROJECT_NAME`

### `--source-home` / `-s` (path)
Set the common [`Source Home`](../home_folder/source_home.md) path for all [supported executables](../control_env/index.md#supported-executables).

- Default: Current working directory
- Supported control environment(s): All
- Environment variable(s): None

??? note
    The [control environment](../control_env/index.md#environment-variables) will set `CETK_SOURCE_HOME` during run-time,
    even though [`Source Home`](../home_folder/source_home.md) cannot be [configured](config.md) by environment variable (or TOML file).

### `--output-home` / `-o` (path)
Set the common [`Output Home`](../home_folder/output_home.md) path for all [supported executables](../control_env/index.md#supported-executables).

- Default: `<Source Home>/artifacts`
- Supported control environment(s): All
- Environment variable(s): `CETK_OUTPUT_HOME`

??? note
    The [control environment](../control_env/index.md#environment-variables) will set `CETK_OUPUT_HOME` during run-time,
    regardless from which [configuration entity](config.md) `OUTPUT HOME` has been configured.

### `--environment` (choice)
Define the control environment to be used.

- Choices: `native`, `docker`, `cloud`
- Default: `native`
- Supported control environment(s): All
- Environment variable(s): `CETK_ENVIRONMENT`

??? note
    The [control environment](../control_env/index.md#environment-variables) will set `CETK_ENVIRONMENT` during run-time,
    regardless from which [configuration entity](config.md) `environment` has been configured.

---

### `--verbose` / `-v`
Show log messages in the terminal (stderr).

- Default: disabled
- Supported control environment(s): All
- Environment variable(s): `CETK_VERBOSE`, `CETK_ENABLE_VERBOSE`[^1]

### `--enable-file-logging`
Enable logging into a file (for default file location, see `--log-file`)

- Default: enabled (by TOML configuration file)
- Supported control environment(s): All
- Environment variable(s): `CETK_FILE_LOGGING`, `CETK_ENABLE_FILE_LOGGING`[^1]

### `--log-file` (file path)
Specify different path/file name for the log file (if enabled).

- Default: `<Output Home>/cetk.log`
- Supported control environment(s): All
- Environment variable(s): `CETK_LOG_FILE`

---

### `--compose-file` (file path)
Docker compose file to be used for Docker compose environment.
Option can be used several times.

- Default: None
- Supported control environment(s): native, docker
- Environment variable(s): `CETK_COMPOSE_FILES`

### `--compose-dotenv-file` (file path)
Dotenv (`.env`) file passed to Docker compose environment.

- Default: None
- Supported control environment(s): native, docker
- Environment variable(s): `CETK_COMPOSE_DOTENV_FILE`

### `--compose-executable-name` (str)
Name of the executable to be used to control `compose`.

- Default: `docker`
- Supported control environment(s): native, docker
- Environment variable(s): `CETK_COMPOSE_EXECUTABLE_NAME`

### `--compose-executable-path` (path)
Alternative search path for executable that controls `compose`.

- Default: System/User `PATH`
- Supported control environment(s): native, docker
- Environment variable(s): `CETK_COMPOSE_EXECUTABLE_PATH`

### `--compose-verbose`
Enable verbose mode for compose executable

- Default: disabled
- Supported control environment(s): native, docker
- Environment variable(s): `CETK_COMPOSE_VERBOSE`, `CETK_COMPOSE_ENABLE_VERBOSE`[^1]

---

### `--docker-image` (str)
The name/tag of the control environment Docker image.

- Default: None
- Supported control environment(s): docker
- Environment variable(s): `CETK_DOCKER_IMAGE`

??? note
    The [docker control environment](../control_env/docker.md#environment-variables) will set `CETK_DOCKER_IMAGE` during run-time,
    regardless from which [configuration entity](config.md) `docker image` has been configured.

---

### `--cloud-api-key` (str)
API key to authorize against cETK cloud service. This key can be
obtained from the cloud service "developer" portal as a self-service.

- Default: None
- Supported control environment(s): cloud
- Environment variable(s): `CETK_CLOUD_API_KEY`

### `--cloud-customer-id` (str)
Customer ID to access customer-specific cETK cloud service API. This ID is
given by comlet upon valid/active subscription.

- Default: None
- Supported control environment(s): cloud
- Environment variable(s): `CETK_CLOUD_CUSTOMER_ID`

### `--cloud-add-upload-path` (path)
Additional [`Output Home`](../home_folder/output_home.md) or [`Temp Home`](../home_folder/temp_home.md) path from which files are uploaded to
cETK cloud service as sources (not filtered and non-recursive). Option can be given multiple times.

- Default: None
- Supported control environment(s): cloud
- Environment variable(s): `CETK_CLOUD_ADD_UPLOAD_PATHS`

### `--cloud-force-upload`
Forces upload of sources to cETK cloud service — even if they exist.

- Default: disabled
- Supported control environment(s): cloud
- Environment variable(s): `CETK_CLOUD_FORCE_UPLOAD`, `CETK_CLOUD_ENABLE_FORCE_UPLOAD`[^1]

[^1]: The `ENABLE` environment variable just needs to be defined, its value does not matter to enable the option.
      Whereas the "normal" variable needs to have a truth-y or false-y value