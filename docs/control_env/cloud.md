# Control Environment: Cloud
This control environment encapsulates and delegates the execution of [supported executables](index.md#supported-executables) to a dedicated cloud service provided by comlet.

In contrast to the on premise control environments, this configuration only needs [cetk-cli](../cli/index.md) installed and
configured for the cloud service to be used.

??? info "Active cloud subscription needed"
    To make use of this control environment, an active subscription is needed.
    Feel free to contact [our sales](mailto:sales@comlet.de?subject=cETK Cloud Service Subscription) for further details.

## System Requirements
--8<-- "snippets/control_env_sys_req.md"

## Environment Variables
[See the common environment variables set.](index.md#within-control-environment)

## Configuration
### Mandatory
- `--environment=cloud`
- `--cloud-api-key`: API Key that can be obtained from the cloud service's self-service portal
- `--cloud-customer-id`: Customer ID that is given by comlet upon active cloud subscription[^3]

??? tip
    See [cetk-cli's global options](../cli/global_options.md) for further details.

## Sources Upload
[cetk-cli](../cli/index.md) will upload [`Source Home`](../home_folder/source_home.md) to the cloud service before executing
any [supported executable](index.md#supported-executables). It will also evaluate a hash based on the sources to uniquely
identify them and skip upload if sources already exist[^1].

??? tip
    If an upload shall be forced even though the sources already exist, the [global option](../cli/global_options.md#-cloud-force-upload)
    `--cloud-force-upload` may be used.

If additional files from [`Output Home`](../home_folder/output_home.md) or [`Temp Home`](../home_folder/temp_home.md) shall be uploaded, the [global option](../cli/global_options.md#-cloud-add-upload-path-path)
    `--cloud-add-upload-path` may be used. Files within this path are not filtered by the allowlist but also not recursively considered.  

!!! warning
    Some system or sensitive folders are in general not allowed for sources to be uploaded from.
    This is platform-specific and includes both system root and global config folders as well as
    some tool-specific ones from the user's home.

    There will be an error message indicating that **the source path is not allowed to be uploaded**.
    In such case, it is adviced to move [`Source Home`](../home_folder/source_home.md) into a different base folder.

### Filter Sources for Upload
To prevent uncontrolled upload of any file within [`Source Home`](../home_folder/source_home.md), [cetk-cli](../cli/index.md) uses an allowlist to filter folders and files
based on their relative path within [`Source Home`](../home_folder/source_home.md)[^2].

The default allowlist is part of the [`init` command](../cli/init.md) and may be adjusted to project's needs.

See [`Source Home` for further details](../home_folder/source_home.md#allowlist-file-for-cloud-upload).

## Waiting for the Cloud Service to finish execution task
[cetk-cli](../cli/index.md) polls the status of the execution every 5 seconds and waits a maximum of 3600 seconds (1 hour)
for the execution to be finished (default). If the cloud service does not report the end of the execution within this
time frage, the client application will manually abort it.

The maximum waiting time can be adjusted with the [global option](../cli/global_options.md#-cloud-status-poll-max-timeout-int) `--cloud-status-poll-max-timeout`.

If this option is configured to be zero (`0`), the client application does not abort the execution at all.

??? info
    The cloud service also has a maximum execution time configured to prevent unforeseen execution issues or infinite resource allocation.
    Currently, this timeout is configured as a six-hour maximum and will abort execution if the client application does not.

## Output Download
All artifacts/reports that are produced by any [supported executable](index.md#supported-executables) are downloaded from
the cloud service and stored within the local [Home Folders](../home_folder/index.md) depending on their original configuration.

## Bridging the Cloud Service with the Local SUT
To not expose the SUT to public (Internet) access, the cloud service uses [cESD(s)](../cesd/index.md) to act as a bridge (aka gateway) between
the cloud service and the (local) SUT. It communicates via authenticated and encrypted MQTT v5 over TLS (MQTTS) with the cloud service.
The necessary keys are securely stored on and specific to the cESD per customer.

## Security Considerations
Every request to the cloud service is encrypted (TLS 1.2), authenticated against the API key and authorized within
the cloud service together with the customer ID.

Files uploaded to the cloud service additionally use SHA256 hashes for integrity.

[^1]: Comparable to the commit hash of git
[^2]: Allowlist is defined in git wildmatch patterns
[^3]: Alongside access to the cloud service's self-service portal