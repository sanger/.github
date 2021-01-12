# Project name

(some badges for fun...)

[![made-with-Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](http://commonmark.org)

A short desciption of the project.

## Table of contents [Optional]

> A table of contents if useful for large/busy READMEs, look under the 'Miscellaneous -> Updating the table
> of contents' section for how to generate the table of contents.
> __NB:__ Be sure to check the source of this template for the tags required to automatically generate the table of
> contents: `toc` and `tocstop`.

<!-- toc -->

- [Requirements for development [Mandatory]](#requirements-for-development-mandatory)
- [Getting started [Optional]](#getting-started-optional)
  * [Configuring environment [Optional]](#configuring-environment-optional)
  * [Setup steps [Optional]](#setup-steps-optional)
- [Running [Mandatory]](#running-mandatory)
- [Testing [Mandatory]](#testing-mandatory)
  * [Testing requirements [Optional]](#testing-requirements-optional)
  * [Running tests [Mandatory]](#running-tests-mandatory)
- [Deployment [Mandatory]](#deployment-mandatory)
- [Important section [Optional]](#important-section-optional)
- [Miscellaneous [Mandatory]](#miscellaneous-mandatory)
  * [Troubleshooting [Optional]](#troubleshooting-optional)
  * [Updating the table of contents [Mandatory]](#updating-the-table-of-contents-mandatory)
  * [Less important section [Optional]](#less-important-section-optional)

<!-- tocstop -->

## Requirements for development [Mandatory]

> Any application or service required to develop the application should be specified here in as much detail as is
> reasonable.

_E.g._ The following tools are required for development:

- ruby (version defined in the `.ruby-version`)
- python (use `pyenv` or something similar to install the python version specified in the `Pipfile`)

See the [Troubleshooting](#troubleshooting) section for any commonly encountered installation issues.

## Getting started [Optional]

> Specify anything that is required before being able to run the application.

### Configuring environment [Optional]

> Specify any required `.env` files or environmental variables that need to be set.

_E.g._ Create a `.env` file with the following values:

    ENV_VAR_1 = var1
    ENV_VAR_2 = var2

### Setup steps [Optional]

> Specify if any steps are required to be run in a specific order for the application to be setup correctly.

_E.g._ Install the require gems:

    bundle install

_E.g._ Create the database and seed the database with default data by running:

    bundle exec rails db:setup

## Running [Mandatory]

> Specify how to run the application.

_E.g._ Python

    pipenv shell
    python runner.py

_E.g._ Ruby (Rails)

    bundle exec rails

## Testing [Mandatory]

> Specify how to test the application.

### Testing requirements [Optional]

> Specify if any dependencies (databases, brokers, etc.) need to be up and running before testing can
commence.

### Running tests [Mandatory]

> Specify how to run tests.

_E.g._ Python

    python -m pytest

_E.g._ Ruby (Rails)

    bundle exec spec

## Deployment [Mandatory]

> Specify how a deployment release should be created for this project, i.e. a release tag for an asset
> or to create a Docker image

_E.g._ This project uses a Docker image as the unit of deployment. To create a release for deployment, create a release
in GitHub and wait for the GitHub action to create the Docker image.

The release version should align with the [standards](./standards.md).

## Important section [Optional]

> Use this level of section to specify anything else that is considered important for this application.
## Miscellaneous [Mandatory]

> This section allows for anything that does not clearly fit under the above sections.

### Troubleshooting [Optional]

> This section is especially helpful when requirements or dependecies are prone to be troublesome.

_E.g._ If you are having trouble installing this, try this...

### Updating the table of contents [Mandatory]

> Always include this section so we can keep the table of contents up to date

To update the table of contents after adding things to this README you can use the [markdown-toc](https://github.com/jonschlinkert/markdown-toc)
node module. To run:

    npx markdown-toc -i README.md

### Less important section [Optional]

> Use this level of section to specify anything that is considered less important for this application.
