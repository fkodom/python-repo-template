# {{REPO_NAME}}

## Usage

Create a new repository, using this one as a template.  Then, run the `templatize` script:

```bash
./templatize
```

This replaces all `{{REPO_NAME}}` and similar placeholders, so the repo is properly configured with your project name, your username and email, etc.  Commit the changes, and you're ready to go!

```bash
git add .
git commit -m "Templatize"
git push
```


## Install

```bash
pip install "{{REPO_NAME}} @ git+ssh://git@github.com/{{REPO_OWNER}}/{{REPO_NAME}}.git"

# Install all dev dependencies (tests etc.)
pip install "{{REPO_NAME}}[test] @ git+ssh://git@github.com/{{REPO_OWNER}}/{{REPO_NAME}}.git"

# Setup pre-commit hooks
pre-commit install
```


## Test

Tests run automatically through GitHub Actions.
* Fast tests run on each push.
* Slow tests (decorated with `@pytest.mark.slow`) run on each PR.

You can also run tests manually with `pytest`:
```bash
pytest
# For all tests, including slow ones:
pytest --slow
```


## Release (Optional)

**NOTE**: Requires `publish.yaml` workflow to be enabled., and a valid PyPI token to be set as `PYPI_API_TOKEN` in the repo secrets.

Tag a new release in this repo, and GHA will automatically publish Python wheels.
