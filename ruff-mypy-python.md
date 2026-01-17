# ruff-mypy-python

This workflow can be used to lint and check format with ruff and type check with mypy

| Option | Description | Type | Default | Required |
|-----------------|-------------------------------------------|--------|---------------------|----------|
| lint | Whether or not to lint using ruff | boolean | true | No |
| format | Whether or not to format using ruff | boolean | true | No |
| type_check | Whether or not to type check using mypy | boolean | true | No |
| lint_command | The command to use to lint with ruff | string | 'ruff check .' | No |
| format_command | The command to use to format with ruff | string | 'ruff format . --check' | No |
| type_check_command | The command to use to type check with mypy | string | 'mypy .' | No |
| os | The os to use | string | 'ubuntu-latest' | No |
| python_version | The python version to use | string | '3.13' | No |
| dependency_install_command | The command to use to install the project dependencies | string | 'pip install .' | No |

## Basic setup
```yaml
name: 'Lint & Type Check'

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  linting-and-type-checking:
    name: 'Lint & Type Check'

    uses: Mews/.github/.github/workflows/ruff-mypy-python.yaml@main
    with:
      python_version: '3.13'
      os: 'ubuntu-latest'
```