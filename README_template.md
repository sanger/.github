# Project name

(some badges for fun...)

[![made-with-Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](http://commonmark.org)

A short desciption of the project.

## Table of Contents [Optional]

> A table of contents if useful for large/busy READMEs, look under the 'Miscellaneous -> Updating the table
> of contents' section for how to generate the table of contents.
> __NB:__ Be sure to check the source of this template for the tags required to automatically generate the table of
> contents: `toc` and `tocstop`.

<!-- toc -->

- [Requirements for Development [Mandatory]](#requirements-for-development-mandatory)
- [Getting Started [Optional]](#getting-started-optional)
  * [Configuring Environment [Optional]](#configuring-environment-optional)
  * [Setup Steps [Optional]](#setup-steps-optional)
- [Running [Mandatory]](#running-mandatory)
- [Testing [Mandatory]](#testing-mandatory)
  * [Testing Requirements [Optional]](#testing-requirements-optional)
  * [Running Tests [Mandatory]](#running-tests-mandatory)
- [Formatting and Linting etc. [Mandatory]](#formatting-and-linting-etc-mandatory)
  * [Formatting [Mandatory]](#formatting-mandatory)
  * [Linting [Mandatory]](#linting-mandatory)
  * [Other Tooling (e.g. type checking)](#other-tooling-eg-type-checking)
- [Deployment [Mandatory]](#deployment-mandatory)
- [Important Section [Optional]](#important-section-optional)
- [Miscellaneous [Mandatory]](#miscellaneous-mandatory)
  * [Troubleshooting [Optional]](#troubleshooting-optional)
  * [Updating the Table of Contents [Mandatory]](#updating-the-table-of-contents-mandatory)
  * [Less Important Section [Optional]](#less-important-section-optional)

<!-- tocstop -->

## Requirements for Development [Mandatory]

> Any application or service required to develop the application should be specified here in as much detail as is
> reasonable.

_E.g._ The following tools are required for development:

- ruby (version defined in the `.ruby-version`)
- python (use `pyenv` or something similar to install the python version specified in the `Pipfile`)

See the [Troubleshooting](#troubleshooting) section for any commonly encountered installation issues.

## Getting Started [Optional]

> Specify anything that is required before being able to run the application.

### Configuring Environment [Optional]

> Specify any required `.env` files or environmental variables that need to be set.

_E.g._ Create a `.env` file with the following values:

    ENV_VAR_1 = var1
    ENV_VAR_2 = var2

### Setup Steps [Optional]

> Specify if any steps are required to be run in a specific order for the application to be setup correctly.

_E.g._ Install the require dependencies:

    pipenv install --dev
    OR
    bundle install
    OR
    yarn install

_E.g._ Create the database and seed the database with default data by running:

    bundle exec rails db:setup

## Running [Mandatory]

> Specify how to run the application.

_E.g._ To run the application:

    python runner.py
    OR
    flask run
    OR
    bundle exec rails

## Testing [Mandatory]

> Specify how to test the application.

### Testing Requirements [Optional]

> Specify if any dependencies (databases, brokers, etc.) need to be up and running before testing can
commence.

### Running Tests [Mandatory]

> Specify how to run tests.

_E.g._ To run the test suite:

    python -m pytest
    OR
    bundle exec rspec

## Formatting and Linting etc. [Mandatory]

> Describe how the project is formatted and linted and how to run these checks manually.
>
### Formatting [Mandatory]

> Specify how the project is formatted.

_E.g._ This project is formatted using [black](https://github.com/psf/black). To run formatting
checks, run:

    pipenv run black .

### Linting [Mandatory]

> Specify how the project is linted.

_E.g._ This project is linted using [flake8](https://github.com/pycqa/flake8). To lint the code,
run:

    pipenv run flake8

### Other Tooling (e.g. type checking)

> Specify any other tooling that verifies code quality etc.

_E.g._ This project uses static type checking using the [mypy](https://github.com/python/mypy)
library, to run:

    pipenv run mypy .

## Deployment [Mandatory]

> Specify how a deployment release should be created for this project, i.e. a release tag for an asset
> or to create a Docker image

_E.g._ This project uses a Docker image as the unit of deployment. To create a release for deployment, create a release
in GitHub and wait for the GitHub action to create the Docker image.

The release version should align with the [standards](./standards.md).

## Important Section [Optional]

> Use this level of section to specify anything else that is considered important for this application.
>
## Miscellaneous [Mandatory]

> This section allows for anything that does not clearly fit under the above sections.

### Troubleshooting [Optional]

> This section is especially helpful when requirements or dependecies are prone to be troublesome
> when installing or setting up.

_E.g._ If you are having trouble installing this, try this...

### Updating the Table of Contents [Mandatory]

> Always include this section so we can keep the table of contents up to date

To update the table of contents after adding things to this README you can use the [markdown-toc](https://github.com/jonschlinkert/markdown-toc)
node module. To run:

    npx markdown-toc -i README.md

### Less Important Section [Optional]

> Use this level of section to specify anything that is considered less important for this application.
