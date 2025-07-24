# Default Options
Each executable gets a carefully curated set of default options that is the result of many hours and projects of enterprise
test automation.

## robot

### Tags
#### `not_ready`
Tag to be used for test cases that shall be skipped, i.e., their result is ignored.

#### `no_logging`
Tag for keywords that shall not log anything. This is useful if a keyword handles sensitive data like secrets.

#### `dont_run`
Tag for test cases that shall not be run at all.

### Test Case Randomization
Tests within test suites are randomized regarding their execution order. This is a proven way to identify unwanted side
effects between test cases.

### Run Empty Test Suites
If test cases are selected based on `--include` or `--exclude` this will make sure, test suites do not fail if no test case
has been selected.

### Reports and Logs
#### `cetk_xunit.xml`
Report in xUnit format that can be processed by most of the common CI/CD processors.

#### `cetk_log.html`
Detailed log for every keyword called from every test case in every test suite in HTML format.

#### `cetk_report.html`
Overview/Summary report in HTML format that can be used as a dashboard.

#### `cetk_output.xml`
XML output with all raw information/details in a machine-processable way.

### Global Variables
#### `RESOURCES`
Global variable `${RESOURCES}` that can be used to reference the `resources` sub-folder from [`Source Home`](../home_folder/source_home.md).

### Default Output Directory
[`Output Home`](../home_folder/output_home.md) is set as default output directory where all the [reports and logs](#reports-and-logs) are saved.

### Additions to `PYTHONPATH`
#### `<Source Home>/libraries`
Adds the `libraries` sub-folder from [`Source Home`](../home_folder/source_home.md) as an additional python path.

### Log level
Configures the log level to enable `TRACE` logs but visually show only `INFO` level as default in HTML log.
This makes sure no detail is missed if a test case fails, but the HTML is not overloaded with unnecessary details by default.

## rebot

### Tags
#### `no_logging`
Tag for keywords that shall not log anything. This is useful if a keyword handles sensitive data like secrets.

#### `dont_run`
Tag for test cases that shall not be run at all.

### Process Empty Test Suites
If test suites have no test cases, this will make sure `rebot` will not fail while processing.

### Reports and Logs
#### `cetk_xunit_merged.xml`
Merged xUnit log.

#### `cetk_log_merged.html`
Merged HTML log.

#### `cetk_report_merged.html`
Merged HTML report.

#### `cetk_output_merged.xml`
Merged XML report (raw data).

### Default Output Directory
[`Output Home`](../home_folder/output_home.md) is set as default output directory where all the merged [reports and logs](#reports-and-logs) are saved.

### Additions to `PYTHONPATH`
#### `<Source Home>/libraries`
Adds the `libraries` sub-folder from [`Source Home`](../home_folder/source_home.md) as an additional python path.

### Log level
Configures the log level to enable `TRACE` logs but visually show only `INFO` level as default in HTML log.
This makes sure no detail is missed if a test case fails, but the HTML is not overloaded with unnecessary details by default.

## libdoc

### Additions to `PYTHONPATH`
#### `<Source Home>/libraries`
Adds the `libraries` sub-folder from [`Source Home`](../home_folder/source_home.md) as an additional python path.

### Default Output Documentation File
Defines `<Output Home>/cetk_libdoc.html` as default output file and HTML format.

## testdoc

### Tags
#### `dont_run`
Tag for test cases that shall not be run at all.

### Default Output Documentation File
Defines `<Output Home>/cetk_testdoc.html` as default output file and HTML format.

## robocop

### Default config
Default config for linting that fits perfectly with the beautifier `robotidy`.

### Default Output Report
Defines `<Output Home>/cetk_lint_report.html` as default output report.

## robotidy

### Default config
Default config for beautifying that fits perfectly with the linter `robocop`.
