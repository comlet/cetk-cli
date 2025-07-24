# Home Folder

The concept of `Home Folder` is a folder/file hierarchy with an expected/pre-defined structure that is
externally managed and delivered into the [control environment](../control_env/index.md).

Externally managed means that those folders are not part of the [control environment](../control_env/index.md) itself. This can vary from 
local/temporary folder to folder under the control of (de-)centralized managed versioning control systems like `git`.

???+ warning "Important"
    Test sources and their data are only allowed to be executed from `Source Home` or `Output Home`.

???+ warning "Important"
    Outputs/Artifacts are only allowed to be written to `Source Home`, `Output Home` or `Temp Home`.
