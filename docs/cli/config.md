Configuration can be given by three different entities:

* TOML file within [`Source Home`](../home_folder/source_home.md#configuration-file-for-cetk-cli)
* Environment variables
* [CLI options](global_options.md)

The TOML file has the lowest prio and the CLI options the highest. The TOML file is good to define fallback defaults
and is part of the [`init` command](init.md). Environment variables are good to control CI/CD processes and are documented
together with their respective [global option](global_options.md).

!!! note
    [`Source Home`](../home_folder/source_home.md) can only be configured by CLI option.
