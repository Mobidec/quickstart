# quickstart

<img src="https://raw.githubusercontent.com/Mobidec/quickstart/refs/heads/main/doc/assets/France2030-Logo-1024x576.png" alt="logo">

---

Package under development.


## Useful links

Links to resources and documentation:
- [Documentation](https://mobidec.github.io/quickstart/index.html)
- [GitHub Repository](https://github.com/Mobidec/quickstart.git)
- [Issues](https://github.com/Mobidec/quickstart/issues)
- [Changelog](https://github.com/Mobidec/quickstart/blob/main/CHANGELOG.md)
- [PyPI](https://pypi.org/project/quickstart/)


## Description

This "Python Package" template is a complete template designed to create a Python package according to IFPEN's development standards, deployable internally within IFPEN or on the Cloud. This template provides developers with a Python project architecture in which they can contribute, document, and make it available to all IFPEN developers.

This package includes:
- A unit test structure based on the [Pytest](https://docs.pytest.org/en/stable/) library
- Automatic documentation generation based on the [Sphinx](https://www.sphinx-doc.org/en/master/) library
- A CI/CD pipeline for deploying the Python package to a Python server


## Github Pages

Your automaticly generated documentation (with Sphinx) is [Here](https://mobidec.github.io/quickstart/)


## Python Package Template Architecture


```
.
├── sphinx
│   ├── pages
│   │    └── Directory for pages to include in sphinx documentation
│   ├── notebooks
│   │    └── Directory for Jupyter Notebooks to include in sphinx documentation
│   ├── conf.py
│   │    └── Sphinx documentation configuration file
│   └── index.rst
│        └── Root file for Sphinx documentation, structuring and linking source documents into complete documentation.
├── src
│   └── quickstart
│        ├── __init__.py
│        ├── main.py
│        │    └── Main file of your package, it references what is usable in your package
│        └── module_name
│             ├── __init__.py
│             └── module.py
│                  └── Module file, each module holds a logic of the package
├── tests
│   ├── unit
│   │    └── Directory for unit tests. These tests are run after each push.
│   ├── integration
│   │    └── Directory for integration tests. These tests are run after each push.
│   ├── local
│   │    └── Directory for tests run only locally. These tests are not run with Github actions.
│   └── ignored
│        └── Directory for tests run manually. These tests are ignored by the command pytest.
├── .gitattributes
│    └── Ensures that all text files use LF as the line ending, improving consistency across different development environments.
├── .bumpversion.toml
│    └── Configuration file for bumping the package version
├── .gitignore
│    └── File explicitly instructed for Git to ignore
├── .github
│    └── workflows
│         └── Github Ci/CD files
├── .pre-commit-config.yaml
│    └── Pre-commit configuration file
├── CONTRIBUTING.md
│    └── Contribution guidelines file
├── LICENSE
├── README.md
│    └── File with general information about the project
├── pyproject.toml
│    └── Package configuration file
└── tox.ini
     └── Configuration file for `tox`, used to automate testing and linting tasks across multiple Python environments. This file is configured to use Python 3.12 and runs commands for the linter `ruff` as well as for tests with `pytest`. The specified commands check code style, format files according to defined standards, and run unit tests to ensure the code works as expected. This file is also used to facilitate version management tasks with `bump-my-version`.
```


## Getting Started

### Prerequisites

This project requires **Python 3.12**. Python 3.12 introduces many new features and improvements that are essential for the proper functioning of this project. Ensure that Python is correctly installed on your system by running `python --version`.


### About the `pyproject.toml` File

The `pyproject.toml` file is a central configuration file for the Python project. It contains TOML tables specifying the basic metadata of the project, the dependencies needed to build your project, and specific configurations for the tools used.
The `[project]` table is used to specify the basic metadata of your project, such as dependencies, your name, etc. The `[tool]` table contains sub-tables specific to each tool, such as `[tool.setuptools]` or `[tool.ruff]`. For more information on configuring your `pyproject.toml`, refer to the [Python documentation](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/).


### Installing Dependencies

The `pyproject.toml` file is used to manage the dependencies of this project. To install these dependencies, follow these steps:

1. Open a terminal and navigate to the project directory.
2. Run the command `pip install .` to install the necessary dependencies for the project.

This process ensures that all required dependencies are correctly installed in your environment, allowing you to work on the project with all necessary resources.

To add or modify project dependencies, you must list them in your `pyproject.toml` file under the `dependencies` section.

```bash
dependencies = [
    # add necessary dependencies
    "pytest == 8.0.1",  # example which can be removed
]
```


### Developing the Package

The `CONTRIBUTING.md` file is an essential guide for developing this Python package. It describes the steps to set up the development environment, the coding conventions to follow, and how to submit changes. 
Once your changes are ready, push your contribution to the desired branch to trigger the integration pipeline, which will create the Python package and deploy it to the Python server.
For more details on contributing and best practices, please refer to the `CONTRIBUTING.md` file.


## Using the Python Package

### Installation

If you are using the provided `pip.conf`, you can simply run:

```bash
pip install quickstart
```

Otherwise, you can specify the package index depending on whether you are in an internal (on-premise) or external (cloud) environment.

```bash
# On-premise
pip install quickstart --extra-index-url https://nexus.ifpen.fr/repository/fast-it/simple

# On Cloud
pip install quickstart --extra-index-url https://nexus.fastit.dev/repository/fast-it/simple
```

Alternatively, you can set the package index URL as an environment variable:

```bash
# On-premise
export PIP_EXTRA_INDEX_URL=https://nexus.fastit.dev/repository/fast-it/simple


# On Cloud
export PIP_EXTRA_INDEX_URL=https://nexus.ifpen.fr/repository/fast-it/simple
```

### Example Usage of the Python Package in Your Code

After installation, you can import and use your package and its functions in your Python code:

```python
from package import hello_world

hello_world()
```

To use sub-modules defined in the package:

```python
from package.divider import divide

a = 4.0
b = 2.0

c = divide(4., 2.)
```

These instructions will allow you to access the package and utilize its features effectively and in line with your development configuration.


## License

This project is licensed under the MIT License, which means it is freely usable for personal and commercial purposes. The MIT License is one of the most permissive open source licenses. It allows you to do almost anything with the source code, as long as you retain the original license notice and copyright information when redistributing the software or substantial portions of it. This license comes without any warranties, so the software is provided "as is." For more details, please refer to the included LICENSE file.

---