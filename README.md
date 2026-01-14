# python-repo-template

A simple template for Python projects, with CI/CD configured through GitHub Actions.


## Install

> **Note:** For simplicity, I assume you are using [uv](https://docs.astral.sh/uv/getting-started/installation/), but this project is compatible with any virtual environment or package manager (`pip`, `venv`, `poetry`, `pipenv`, `conda`).

```bash
# Create and activate a new virtual environment
uv venv --python 3.12
source .venv/bin/activate

# Install development dependencies and pre-commit hoooks
uv sync --all-extras
pre-commit install
```


## Tooling

| Tool | Description | Runs on |
| --- | --- | --- |
| [ruff](https://github.com/astral-sh/ruff) | Code linter | - `git commit` (through `pre-commit`) <br> - `git push` <br> - pull requests |
| [ty](https://docs.astral.sh/ty/) | Static type checker | - `git commit` <br> - pull requests |
| [pytest](https://github.com/pytest-dev/pytest) | Unit testing framework | - `git push` <br> - pull requests |
| [twine](https://github.com/pypa/twine) $\dagger$ | PyPI package uploader | - New release (`git tag`) |

> $\dagger$ Requires enabling the `publish.yaml` workflow.  To activate, move the file from `.github/disabled-workflows/publish.yaml.disabled` to `.github/workflows/publish.yaml`, and set a valid PyPI token as `PYPI_API_TOKEN` in the repo secrets.
>
> Then tag a new release of this repo, and GHA will automatically build and publish a Python wheel (`.whl`) to PyPI.
