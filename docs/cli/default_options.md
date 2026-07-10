# Default Options

Each executable gets a carefully curated set of default options that is the result of many hours and projects of enterprise
test automation.

## User Overrides

cetk-cli adds the defaults listed below before forwarding the command to the selected executable.

Defaults marked as **overwritable** are skipped when the user command already contains the same executable option or a documented equivalent option, such as a short alias.

Defaults marked as **fixed** are always added by cetk-cli. They are part of the cETK execution policy and are not removed when the user command contains a similar executable option.

For positional default output files, **overwritable** means that cetk-cli skips the default when it can identify an explicit output target or executable-specific output mode for that executable.

## robot

### Tags

#### `not_ready` (overwritable)

Tag to be used for test cases that shall be skipped, i.e., their result is ignored.

#### `no_logging` (overwritable)

Tag for keywords that shall not log anything. This is useful if a keyword handles sensitive data like secrets.

#### `dont_run` (fixed)

Tag for test cases that shall not be run at all.

### Test Case Randomization (overwritable)

Tests within test suites are randomized regarding their execution order. This is a proven way to identify unwanted side
effects between test cases.

### Run Empty Test Suites (overwritable)

If test cases are selected based on `--include` or `--exclude` this will make sure, test suites do not fail if no test case
has been selected.

### Reports and Logs

#### `cetk_xunit.xml` (overwritable)

Report in xUnit format that can be processed by most of the common CI/CD processors.

#### `cetk_log.html` (overwritable)

Detailed log for every keyword called from every test case in every test suite in HTML format.

#### `cetk_report.html` (overwritable)

Overview/Summary report in HTML format that can be used as a dashboard.

#### `cetk_output.xml` (overwritable)

XML output with all raw information/details in a machine-processable way.

### Global Variables

#### `RESOURCES` (fixed)

Global variable `${RESOURCES}` that can be used to reference the `resources` sub-folder from [`Source Home`](../home_folder/source_home.md).

### Default Output Directory (overwritable)

[`Output Home`](../home_folder/output_home.md) is set as default output directory where all the [reports and logs](#reports-and-logs) are saved.

### Additions to `PYTHONPATH`

#### `<Source Home>/libraries` (fixed)

Adds the `libraries` sub-folder from [`Source Home`](../home_folder/source_home.md) as an additional python path.

### Log level (overwritable)

Configures the log level to enable `TRACE` logs but visually show only `INFO` level as default in HTML log.
This makes sure no detail is missed if a test case fails, but the HTML is not overloaded with unnecessary details by default.

## rebot

### Tags

#### `no_logging` (overwritable)

Tag for keywords that shall not log anything. This is useful if a keyword handles sensitive data like secrets.

#### `dont_run` (fixed)

Tag for test cases that shall not be run at all.

### Process Empty Test Suites (overwritable)

If test suites have no test cases, this will make sure `rebot` will not fail while processing.

### Reports and Logs

#### `cetk_xunit_merged.xml` (overwritable)

Merged xUnit log.

#### `cetk_log_merged.html` (overwritable)

Merged HTML log.

#### `cetk_report_merged.html` (overwritable)

Merged HTML report.

#### `cetk_output_merged.xml` (overwritable)

Merged XML report (raw data).

### Default Output Directory (overwritable)

[`Output Home`](../home_folder/output_home.md) is set as default output directory where all the merged [reports and logs](#reports-and-logs) are saved.

### Additions to `PYTHONPATH`

#### `<Source Home>/libraries` (fixed)

Adds the `libraries` sub-folder from [`Source Home`](../home_folder/source_home.md) as an additional python path.

### Log level (overwritable)

Configures the log level to enable `TRACE` logs but visually show only `INFO` level as default in HTML log.
This makes sure no detail is missed if a test case fails, but the HTML is not overloaded with unnecessary details by default.

## libdoc

### Additions to `PYTHONPATH`

#### `<Source Home>/libraries` (fixed)

Adds the `libraries` sub-folder from [`Source Home`](../home_folder/source_home.md) as an additional python path.

### Default Output Documentation File (overwritable)

Defines `<Output Home>/cetk_libdoc.html` as default output file and HTML format.

??? note
    This default is not added when the user command uses a `libdoc` special command or an explicit output target ending with `.html`, `.htm`, `.xml`, `.json`, `.spec`, or `.libspec`.

## testdoc

### Tags

#### `dont_run` (fixed)

Tag for test cases that shall not be run at all.

### Default Output Documentation File (overwritable)

Defines `<Output Home>/cetk_testdoc.html` as default output file and HTML format.

??? note
    This default is not added when the user command contains an explicit output target ending with `.html` or `.htm`.

## testdoc_ext (beta)

Note: `testdoc_ext` requires `robotframework-testdoc>=0.6.4`.

### Tags

#### `dont_run` (fixed)

Tag for test cases that shall not be run at all.

### Default Output Documentation (overwritable)

Defines HTML as default output file format by `--output-format html` and defines `<Output Home>/cetk_testdoc_ext.html` as default output file.

??? note
    The default output format and default output file are a single overwritable default group.

    The group is not added when the user command:

    - sets `--output-format` or `-f`
    - uses `--mkdocs`
    - contains an explicit output target ending with `.html`, `.htm`, or `.json`

## robocop

### Default config (overwritable)

Default config for linting and formatting[^1].

??? note
    The integrated default config is maintained for Robocop 8.x. The Robocop executable remains usable with older Robocop major versions, but those versions may require a project-specific config with the wrapped executable's `--config` option.

### Default Output Report (overwritable)

Defines `<Output Home>/cetk_lint_report.txt` as default output report.

[^1]: Formerly done by the dedicated, yet deprecated executable `robotidy`
