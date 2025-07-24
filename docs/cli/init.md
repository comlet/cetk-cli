# Initializing Source Home

````shell
cetk init
````

This will add the common [folder structure](../home_folder/source_home.md#expected-folderfile-structure), incl. a [TOML configuration](../home_folder/source_home.md#configuration-file-for-cetk-cli) file with defaults and the [cloud service upload
allowlist file](../control_env/cloud.md#filter-sources-for-upload) to the **current working directory**.

!!! note
    Init will overwrite existing files

## Options

### `--help` / `-h`
Show the help message and exit.

### `--path` / `-p`
Path to init [`Source Home`](../home_folder/source_home.md#expected-folderfile-structure). Defaults to current working directory.

### `--config-only`
Generate/Overwrite TOML configuration file and cloud upload allowlist only.
