# Poetry

## What is Poetry?

### Poetry is a dependency manager and packaging tool for Python. It helps you:

 - Create and manage Python projects

- Handle virtual environments

- Manage dependencies

- Publish your Python packages to PyPI

#### It aims to simplify Python project management.

 ## Part 1: Installation and Setup

 - Step 1: Install Poetry
 ```
 curl -sSL https://install.python-poetry.org | python3 -

 ```
 - This installs Poetry under:
 ```
 $HOME/.local/bin
 ```
 - Add Poetry to Your PATH
 ##### For zsh (default on new macOS versions):
 ```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zprofile
source ~/.zprofile

 ```
- Verify Installation
```
poetry --version

```
## Part 2: Creating a New Project

- Create a Project
```
poetry new my_project

```
- This creates:
```
my_project/
├── pyproject.toml  ← Metadata & dependencies
├── my_project/
│   └── __init__.py ← Your main code
└── tests/
    └── test_my_project.py

```
#### Why:
```
This is better than manually setting up a folder. Poetry creates a standard structure, so you don’t have to.
```
## Part 3: Project Configuration (pyproject.toml)
- Your pyproject.toml looks like this:
```
[tool.poetry]
name = "my_project"
version = "0.1.0"
description = ""
authors = ["Anuj Patwa <anuj@example.com>"]

[tool.poetry.dependencies]
python = "^3.10"

[tool.poetry.dev-dependencies]
pytest = "^7.0"

```
- How to Add Dependencies:
```
poetry add requests
poetry add pandas@^1.5

```
- Add Dev Dependencies:
```
poetry add --dev black

```
#### Why:
```
It replaces the need for requirements.txt, setup.py, and Pipfile.

You define everything in one place.

It automatically resolves dependency conflicts.


```
## Part 4: Virtual Environments
- Poetry automatically creates a virtual environment when you run:
```
poetry install

```
- To activate it:
```
- poetry self add poetry-plugin-shell
- pip install poetry-plugin-shell
- poetry shell

```
- To run a command inside the venv:
```
poetry run python script.py

```
#### Why:
```
Isolates your project environment so you don’t pollute your global Python packages.

```
## Part 5: Running & Testing Code
- Example: Add Some Code
- Edit my_project/__init__.py:
```
def add(a, b):
    return a + b

```
- Edit tests/test_my_project.py:
```
from my_project import add

def test_add():
    assert add(2, 3) == 5

```
- Run Tests:
```
- poetry add --dev pytest
- poetry run pytest

```
## Part 6: Building & Publishing
- Build the Package
```
poetry build

```
- Output:
```
dist/
  my_project-0.1.0.tar.gz
  my_project-0.1.0-py3-none-any.whl

```
- Publish to PyPI
- First, authenticate:
```
poetry config pypi-token.pypi <your_token>

```
Then:
```
poetry publish --build
 
```
#### When:
```
When you're building a library or CLI tool you want to share or reuse.
```
## Part 7: Advanced Features
-  Lock Dependencies
```
poetry lock
```
- This creates poetry.lock, pinning exact versions.
- Export Requirements.txt
```
poetry export -f requirements.txt --output requirements.txt

```
#### Useful when deploying to environments without Poetry.



