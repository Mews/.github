
# format-python

This is a workflow that, when ran, will run the code formater [black](https://pypi.org/project/black/) along with [isort](https://pypi.org/project/isort/) to format your code according to [PEP8](https://peps.python.org/pep-0008/). It will then open a pull request with the fixes to the code, or directly commit them. (Default is opening a pull request)

These are the available options.
| Option             | Description                                                                                                              | Type    | Default                                                                                                                                                                                    | Required |
|--------------------|--------------------------------------------------------------------------------------------------------------------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| black_args         | The options to pass to black                                                                                             | string  | --verbose                                                                                                                                                                                  | No       |
| isort_args         | The options to pass to isort                                                                                             | string  | N/A                                                                                                                                                                                        | No       |
| commit_changes     | Whether or not to commit the formated files directly without a pull request                                              | boolean | false                                                                                                                                                                                      | No       |
| pull_request_title | The title for the pull request created by the action                                                                     | string  | Format code with black and isort                                                                                                                                                           | No       |
| pull_request_body  | The body for the pull request created by the action                                                                      | string  | There are some python formatting issues in <commit SHA>. This pull request fixes those using [black](https://pypi.org/project/black/) along with [isort](https://pypi.org/project/isort/). | No       |
| commit_message     | The message for the commit with the formatted file changes.<br>Used both in the pull request and when commiting directly | string  | Formated code with black and isort                                                                                                                                                         | No       |
| commiter_username  | The username to register in git (not shown in commit)                                                                    | string  | Formatter                                                                                                                                                                                  | No       |
| commiter_email     | The email of the user shown in the commit                                                                                | string  | github-actions[bot]@users.noreply.github.com                                                                                                                                               | No       |

The default `commiter_email` option refers to the github-actions[bot] account.

## Basic setup
**You must give the job `contents: write` and `pull-requests: write` permissions to use this workflow**
```yml
name: Format code with black

on:
  push:
    branches: [ "main" ]

jobs:
  format:
    name: Format code

    permissions:
      contents: write
      pull-requests: write

    uses: Mews/.github/.github/workflows/format-python.yaml@main
```