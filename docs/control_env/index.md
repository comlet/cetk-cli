# Control Environments

Embedded TestKit's control environment is a logical entity that is able to run [supported executables](#supported-executables) for test
automation and in different encapsulation flavors.

It takes [`Source Home`](../home_folder/source_home.md) as input and [`Output Home`](../home_folder/output_home.md) as output folder for every run executable. Connections to the SUT
are established either by the on premise host interfaces and/or by network via [cESD](../cesd/index.md)[^2]. 

## Supported Executables

* [Robot Framework](https://robotframework.org/){target="_blank"} Version 6/7
    * robot, rebot, testdoc, libdoc
* [Tidy](https://github.com/MarketSquare/robotframework-tidy){target="_blank"} Version 4.x
    * robotidy
* [Robocop](https://github.com/MarketSquare/robotframework-robocop){target="_blank"} Version 5.x
    * robocop

## Encapsulation Flavors

* [Native](native.md) (On Premise)
* [Docker](docker.md) (On Premise)
* [Cloud](cloud.md) (Testing as a Service)

## Environment Variables
The Following environment variables are set and available during the execution with [cetk-cli](../cli/index.md)[^5]:

### On The Host
As in: "_The host that is using [cetk-cli](../cli/index.md) to run [supported executables](#supported-executables)_" 

* `CETK_SOURCE_HOME`: absolute path to [`Source Home`](../home_folder/source_home.md)
* `CETK_SOURCE_HOME_POSIX`: absolute path to [`Source Home`](../home_folder/source_home.md) in posix format[^1][^3]
* `CETK_OUTPUT_HOME`: absolute path to [`Output Home`](../home_folder/output_home.md)
* `CETK_OUTPUT_HOME_POSIX`: absolute path to [`Output Home`](../home_folder/output_home.md) in posix format[^1][^4]
* `CETK_TMP_HOME`: absolute path to [`Temp Home`](../home_folder/temp_home.md)
* `CETK_ENVIRONMENT`: one of the following: `native`, `docker`, `cloud`

### Within Control Environment
* `CETK_SOURCE_HOME`: absolute path to [`Source Home`](../home_folder/source_home.md)
* `CETK_OUTPUT_HOME`: absolute path to [`Output Home`](../home_folder/output_home.md)
* `CETK_TMP_HOME`: absolute path to [`Temp Home`](../home_folder/temp_home.md)
* `CETK_ENVIRONMENT`: one of the following: `native`, `docker`, `cloud`

[^1]: Only available for on premise control environments
[^2]: Connections via cESD are the only ones currently supported by the cloud control environment
[^3]: If the host platform is already posix (e.g., Linux) then this is the same as `CETK_SOURCE_HOME`
[^4]: If the host platform is already posix (e.g., Linux) then this is the same as `CETK_OUTPUT_HOME`
[^5]: If any of those variables have been used to [configure cetk-cli](../cli/config.md), they may be updated during execution