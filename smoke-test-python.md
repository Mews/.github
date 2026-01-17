# smoke-test-python

This is a workflow that performs a "smoke test", basically a very preliminary test that just tries to install the package from the files and import it

| Option          | Description                               | Type   | Default             | Required |
|-----------------|-------------------------------------------|--------|---------------------|----------|
| package_name    | The package name to try to import         | string | N/A                 | Yes      |
| install_command | The command to use to install the package | string | 'pip install .'     | No       |
| python_versions | The python versions to use                | string | '["3.12"]'          | No       |
| os_list         | The operating systems to use              | string | '["ubuntu-latest"]' | No       |

## Basic setup
```yaml
name: Tests

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  call-run-python-tests:
    name: Run tests

    uses: Mews/.github/.github/workflows/smoke-test-python.yaml@main
    with:
      package_name: 'mypackage'
      python_versions: '["3.10", "3.12"]'
      os_list: '["ubuntu-latest", "windows-latest", "macos-latest"]'
```