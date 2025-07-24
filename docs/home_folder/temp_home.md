# Temp Home

`Temp Home` is a platform- and user-specific folder that can be used to save interim output results to before finally
saving them into [`Output Home`](../home_folder/output_home.md).

During running a [supported executable](../control_env/index.md#supported-executables) within a [control environment](../control_env/index.md),
this folder can be read by the environment variable `CETK_TMP_HOME`.

## Path Evaluation
Path evaluation for `Temp Home` is done in the following prio (top/down) and order (left/right):

- Environment variables
    - `TMPDIR`, `TEMP`, `TMP`
- Platform-specific directories
    - On Windows `C:\TEMP`, `C:\TMP`, `\TEMP` or `\TMP`
    - On all other platforms `/tmp`, `/var/tmp` or `/usr/tmp`
- Current working directory