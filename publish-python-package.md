# publish-python-package

A workflow to build the wheels and upload the package to pypi, using trusted publishing


| Option | Description | Type | Default | Required |
|--------------------|-------------------------------------------------------|--------|-----------------|----------|
| python_version | Python version to use for build | string | '3.13' | No |
| os | OS to run the build on | string | 'ubuntu-latest' | No |
| pypi_url | The repository URL to upload the package to | string | 'https://upload.pypi.org/legacy/' | No |
| pypi_environment | The name of the GitHub Environment (for OIDC) | string | 'pypi' | No |


***Important:***\
To use this workflow, you must configure **Trusted Publishing** on PyPI

1. **On PyPI:** Go to **Manage Project** > **Publishing** > **Add a Trusted Publisher**.
2. **Repository:** Set to your repository.
3. **Workflow Name:** Set to the filename of your caller workflow (e.g., `release.yml`).
4. **Environment:** Set to `pypi`.

---

## Basic setup

```yaml
name: Publish to PyPi

on:
  release:
    types: [published]

jobs:
  publish:
    uses: Mews/.github/.github/workflows/publish-python-package.yaml@main
    with:
      python_version: '3.13'
      os: 'ubuntu-latest'
    permissions:
      id-token: write
      contents: read
```
