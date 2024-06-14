
# run-python-tests

This is a workflow that can be used to run tests using pytest on a matrix of various python versions and operating systems.

These are the available options:

| Option                  | Description                                                                                                                                                    | Type    | Default             | Required |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|---------------------|----------|
| tests_dir               | The directory where pytest will look at for tests                                                                                                              | string  | N/A                 | Yes      |
| pytest_cpus             | How many cpu cores to use when running tests                                                                                                                   | number  | 1                   | No       |
| python_versions         | The python versions to use to run tests                                                                                                                        | string  | '["3.12"]'          | No       |
| os_list                 | The operating systems to use to run tests                                                                                                                      | string  | '["ubuntu-latest"]' | No       |
| create_coverage_comment | Wether or not to use the [python-coverage-comment](https://github.com/py-cov-action/python-coverage-comment-action/tree/v3/) action to create coverage reports | boolean | false               | No       |
| extra_pytest_arguments  | Any other arguments to pass to pytest                                                                                                                          | string  | N/A                 | No       |

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

    permissions:
      contents: write

    uses: Mews/.github/.github/workflows/run-python-tests.yaml@main
    with:
      tests_dir: "tests/"
      python_versions: '["3.10", "3.12"]'
      os_list: '["ubuntu-latest", "windows-latest", "macos-latest"]'
      create_coverage_comment: true
```

## Notes for creating coverage comment
If you're going to create a coverage comment through the `create_coverage_comment` option, you must give contents write permissions to the job through:
```yaml
permissions:
    contents: write
```

And you must have a `.coveragerc` file with the following option:
```
[run]
relative_files = true
```