# {{REPO_NAME}}

A simple template for Python projects, with CI/CD configured through GitHub Actions.  Compatible with any virtual environment manager (e.g. `uv`, `venv`, `pyenv`, `poetry`, `conda`).


## Usage

1. Create a new repository, using this one as a template.
2. Install and open [Gemini CLI](https://github.com/google-gemini/gemini-cli), then run the `/templatize` command:
    ```bash
    gemini run /templatize
    ```


## Install

> **Note:** For simplicity, I assume you are using [uv](https://docs.astral.sh/uv/getting-started/installation/), but this project is compatible with any virtual environment or package manager (`pip`, `venv`, `poetry`, `pipenv`, `conda`).

If you have not already, create and activate a virtual environment for this project:
```bash
uv venv --python 3.12
source .venv/bin/activate
```

Then, install the package:
```bash
uv sync
```

### For Developers

If you plan to contribute to the project, you should also install development dependencies and pre-commit hoooks:
```bash
uv sync --all-extras
pre-commit install
```


## Tooling

| Tool | Description | Runs on |
| --- | --- | --- |
| [black](https://github.com/psf/black) | Code formatter | - `git commit` (through `pre-commit`) <br> - `git push` <br> - pull requests |
| [ruff](https://github.com/astral-sh/ruff) | Code linter | - `git commit` (through `pre-commit`) <br> - `git push` <br> - pull requests |
| [pytest](https://github.com/pytest-dev/pytest) | Unit testing framework | - `git push` <br> - pull requests |
| [mypy](https://github.com/python/mypy) | Static type checker | - `git push` <br> - pull requests |
| [pre-commit](https://github.com/pre-commit/pre-commit) | Pre-commit hooks | - `git commit` |
| [twine](https://github.com/pypa/twine) $\dagger$ | PyPI package uploader | - New release (`git tag`) |

> $\dagger$ Requires enabling the `publish.yaml` workflow.  To activate, move the file from `.github/disabled-workflows/publish.yaml.disabled` to `.github/workflows/publish.yaml`, and set a valid PyPI token as `PYPI_API_TOKEN` in the repo secrets.
>
> Then tag a new release of this repo, and GHA will automatically build and publish a Python wheel (`.whl`) to PyPI.
