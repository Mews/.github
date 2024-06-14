
# run-python-tests

This is a workflow that, when ran, will run the code formater [black](https://pypi.org/project/black/) along with [isort](https://pypi.org/project/isort/) to format your code according to [PEP8](https://peps.python.org/pep-0008/) and automatically commit it to your repo.

These are the available options.
| Option            | Description                                           | Type   | Default                                      | Required |
|-------------------|-------------------------------------------------------|--------|----------------------------------------------|----------|
| black_args        | The options to pass to black                          | string | --verbose                                    | No       |
| isort_args        | The options to pass to isort                          | string | N/A                                          | No       |
| commiter_username | The username to register in git (not shown in commit) | string | Formatter                                    | No       |
| commiter_email    | The email of the user shown in the commit             | string | github-actions[bot]@users.noreply.github.com | No       |

The default `commiter_email` option refers to the github-actions[bot] account.

## Basic setup
**You must give the job `contents: write` permissions to use this workflow**
```yml
name: Format code with black

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  format:
    name: Format code

    permissions:
      contents: write

    uses: Mews/.github/.github/workflows/format-python.yaml@main
```