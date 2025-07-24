# Command Line Interface

`cetk-cli` is a headless, single-file command line interface delivered as platform-specific binary.

Its purpose is to act as the sole interface for all supported [control environments](../control_env/index.md) and [supported executables](../control_env/index.md#supported-executables).
It makes it easy to be used manually in a local dev scenario as well as within a continuous testing context, automated by a CI/CD pipeline.

Switching from running test automation [locally](../control_env/native.md) or running [encapsulated within a Docker container](../control_env/docker.md) or even without
the need for dedicated infrastructure [within our cloud service](../control_env/cloud.md), is as easy as changing an [environment variable](global_options.md#--environment-choice).

It defines [defaults](default_options.md) for every detail of the test automation process to maintain test and product quality on enterprise level
that is based on years of experience while being flexible enough to be adjusted to every project or product. 

Last but not least, it preserves the user experience of its [supported executables](../control_env/index.md#supported-executables)
as much as possible to also preserve the knowledge of user's already familiar with those.

For general usage information, `cetk-cli` has a [general help](global_options.md#--help---h)


````shell
cetk --help
````

as well as every sub-command

````shell
cetk [init|run] --help
````
