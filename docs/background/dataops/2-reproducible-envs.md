# Reproducible Development Environments

Having gone over some of the history and philosophy of DataOps/DevOps, let's start examining what this looks like in practice.

This page contains two sections: a section on what Dev Containers accomplish for us and why they are advocated for in this class, and a high-level outline of some of the common roadblocks and challenges that teams might encounter when trying to design a development environment using steps--these are challenges that Dev Containers aim to automate and standardize away.

## `devcontainer.json`

To illustrate what Dev Containers do for us, let's take a look at the `devcontainer.json` file in our `.devcontainer` directory. This file is the configuration file for a [Dev Container](https://containers.dev), and among other things, it tells Codespaces/Docker what dependencies need to be installed in our isolated environment.

Check out the annotated configuration below.

```json title=".devcontainer/devcontainer.json"
{
	"name": "CSE314A",
	"image": "mcr.microsoft.com/devcontainers/python:1-3.11-bullseye", // (1)
	"features": { //(2)
		"ghcr.io/devcontainers-contrib/features/mkdocs:2": { // (3)
			"plugins": "mkdocs-material markdown-captions mkdocstrings[python]"
		},
		"ghcr.io/devcontainers-contrib/features/poetry:2": {}, // (4)
		"ghcr.io/devcontainers-contrib/features/pre-commit:2": {}, // (5)
		"ghcr.io/devcontainers-contrib/features/ruff:1": {}, // (6)
		"ghcr.io/eitsupi/devcontainer-features/duckdb-cli:1": {}, // (7)
		"ghcr.io/devcontainers-contrib/features/black:2": {} // (8)
	},
	"postCreateCommand": "poetry install && pre-commit install", // (9)
	"runArgs": [ // (10)
		"--name",
		"CSE314A_dev"
	],
	"customizations": { // (11)
		"vscode": {
			"extensions": [
				"ms-python.python",
				"ms-python.vscode-pylance",
				"tamasfe.even-better-toml", // (12)
				"GitHub.copilot",
				"charliermarsh.ruff",
				"ms-toolsai.jupyter",
				"ms-python.black-formatter",
				"yzhang.markdown-all-in-one"
			],
			"settings": {
				"yaml.schemas": {
					"https://squidfunk.github.io/mkdocs-material/schema.json": "mkdocs.yml"
				},
				"yaml.customTags": [
					"!ENV scalar",
					"!ENV sequence",
					"tag:yaml.org,2002:python/name:materialx.emoji.to_svg",
					"tag:yaml.org,2002:python/name:materialx.emoji.twemoji",
					"tag:yaml.org,2002:python/name:pymdownx.superfences.fence_code_format"
				],
				"python.testing.pytestArgs": [
					"tests"
				],
				"python.testing.unittestEnabled": false,
				"python.testing.pytestEnabled": true,
				"python.defaultInterpreterPath": ".venv/bin/python", // (13)
				"files.insertFinalNewline": true,
				"python.editor.defaultFormatter": "ms-python.black-formatter"
			}
		},
		"codespaces": {
			"repositories": {
				"wustl-data/fl23": {
					"permissions": {
						"contents": "read"
					}
				}
			}
		}
	}
}

```

1. The `image` field tells Codespaces/Docker what base _image_, hosted in a public Container repository, we will to use to build our base Dev Container. This particular image installs a particular version of Python (3.11 in our case!). This takes away the need to juggle different Python installations on our local machine, and ensures that we are all using the same version of Python.
2. _Features_ are essentially "add-ons" for our base container image. They are generally more narrow in scope than the base image and are designed to build on the base image and each other. This section installs some key tools for us automatically; check the annotations for an explanation of each. A diverse list of available features is available at [containers.dev/features](https://containers.dev/features). Imagine how much time it would take to install all of these tools manually, even if everything worked right away! Dev Container features can automate these installations for us.
3. _MkDocs_ is a tool for generating website HTML from Markdown documents in the `docs/` directory. It's how our course webpage is generated. Run `mkdocs serve` to try it out in your environment! Note that we define a few mkdocs extensions here-- to see what customization options are available for a feature, check out its reference page on [containers.dev/features](https://containers.dev/features).
4. _Poetry_ is a Python package and virtual environment manager. We will discuss how we use Poetry in more detail throughout the course.
5. _Pre-commit_ is a tool for running code quality checks and tests before you commit your code. This will help you become more well-versed in Python best practices and will help you avoid common mistakes, as well as help me to evaluate your code by standardizing the format and automating some basic checks.
6. _Ruff_ is an extremely fast and modern _linter_ for Python. Linters are tools that identify syntax and formatting errors extremely quickly so that, for example, your IDE can identify them and provide you with feedback as you type. Ruff is a fast and modern alternative to more traditional linting tools such as flake8 and pylint.
7. _DuckDB_ is a lightweight, in-memory SQL database that we will use for most of our SQL work. It is a powerful Database Managment System (DBMS) for writing SQL queries. It is much faster for analytical queries, has many helpful syntax features and data format conversion features, and is much easier to set up than a traditional SQL database (similar to SQLite). This feature installs DuckDB and the CLI for us.
8. _Black_ is a Python _formatter_. Similarly to a linter, it checks the format of our code, but unlike a linter, it will automatically fix any formatting errors for us. This will help us to write more consistent and idiomatic code that is more easily readable for experienced Python programmers. This is run as one of your pre-commit checks.
9. The `postCreateCommand` field tells Codespaces/Docker what commands to run after the container is created. In this case, we are installing our Python dependencies and setting up our pre-commit checks. There are other "lifecycle commands" that can run commands at various points in the container lifecycle; for more details check out the [.devcontainer reference at containers.dev](https://containers.dev/implementors/json_reference/).
10. This line is mostly unimportant-- the runArgs define arguments to Docker for the build command. Here we are naming the container so that it shows up with a nice name in Docker Desktop.
11. _Customizations_ allow us to configure how some third party tools (namely, at this point, VS Code and Codespaces), behave in our Dev Container Here we are configuring VS Code's IDE settings and declaring its extensions as well as configuring Codespaces to give us read access to the course repository.
12. This is a lightweight VS Code extension that improves the syntax highlighting for TOML files, which are used for configuration in Python projects (e.g. in `pyproject.toml`). This is the kind of thing that can slip under the radar for developers getting started, but is easy to configure with a Dev Container so that it comes automatically.
13. This is an important setting that lets VS code know which virtual environment it should set as the default-- that way it wont give us erroneous linting warnings about missing packages, it chooses the right virtualenv for other extensions like Jupyter, etc.


## Common Roadblocks

_Development environments_ are the set of tools and configurations that a developer uses to write and test code. Traditionally, these environments are often expected to be installed by the individual developer on their local machine. The manual installation of development dependencies gives rise to a variety of problems at various levels of software:

### OS-level concerns

- Package/Application installation and management
    - Windows: winget, OSX: brew, Ubuntu: apt
- Environment variables
    - PATH, Containers, text files
- File permissions
    - sudo, chmod, chown, "Run as Administrator"
- Shell configuration
    - bash/.bashrc, zsh/.zshrc

### Language-level concerns

- Language installation and version management
- Package management
    - Virtual environments
    - Dependency declaration & resolution
- Builds
- Testing
- Debugging

!!! note "Conda and Jupyter"

    Conda is a cross-language/cross-platform package manager, and will only be strictly necessary in this course if you would like to use it for a third-party package that requires it or only provides documentation for conda setups. If this is the case for you or if you just prefer conda, you will likely want to look into adjusting your dev container and using mamba for compatibility/performance reasons.

    Most of you are likely coming from Jupyter-centric development environments. While notebooks are great for experimentation and managing intermediate state, they are not great for reproducibility and collaboration. We will be using Jupyter in this course, but only as a tool for experimentation, exploration, and demonstration. All of your submitted code **must** be written in `.py` files, and all of your code should be runnable from the command line. This will make your code more stable, portable and easier to test and debug. If you really love developing in the Jupyter interface, you might want to look into tools like [nbdev](https://nbdev.fast.ai/) which provide better infrastructural support for Jupyter-centric development.

### Data concerns

- Storage and retrieval
- Installation, authentication, and configuration
- Seed data, test data, production data
- Database migrations

### Deployment concerns

- Containerization
- Config as Code
- Continuous delivery

### Application-level concerns

- Running services
- Interacting with the program
- Logging
- Feedback tools
- Documentation
- Authentication

### Collaboration concerns

- Version control
- Code review
- Issue tracking, feature requests, bug reports
- Continuous integration
- Barrier to entry
