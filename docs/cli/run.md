# Running Executables

````shell
cetk run [supported executable] ...
````

Since this is the default sub-command of `cetk-cli`, `run` can also be omitted:

````shell
cetk [supported executable] ...
````

## Options

The options and arguments after the given [supported executable](../control_env/index.md#supported-executables) (represented
as `...` above) are the same as the executable offers when run by itself.

??? example "Example to print the usage information of `robot`"
    ````shell
    cetk robot --help
    ````