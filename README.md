# Default community health files

[Default community health](https://help.github.com/en/github/building-a-strong-community/creating-a-default-community-health-file) files for Sanger.

> GitHub will use and display default files for any public repository owned by the account that does not have its own file of that type in any of the following places:
>
> * the root of the repository
> * the .github folder
> * the docs folder
>
> For example, anyone who creates an issue or pull request in a public repository that does not have its own CONTRIBUTING file will see a link to the default CONTRIBUTING file. If a repository has any files in its own `.github/ISSUE_TEMPLATE` folder, including issue templates or a `config.yml` file, none of the contents of the default `.github/ISSUE_TEMPLATE` folder will be used.
>
> Default files are not included in clones, packages, or downloads of individual repositories because they are stored only in the `.github` repository.

<br />

# 🛠️ GitHub Actions Strategy in PSD

## Overview

To streamline and modularise our CI/CD processes, we now follow a **standardised and reusable approach** to GitHub Actions. This design revolves around two key concepts:

- ✅ **Composite Actions** stored in the `.github/actions` folder.
- 🔁 **Reusable Workflows** stored in the `.github/workflows` folder.

This structure allows for **cleaner**, **more maintainable**, and **DRY-compliant (Don't Repeat Yourself)** automation practices across all repositories in our organisation.

---

## ✨ Why We Changed Our Approach

Previously, many of our repositories duplicated similar GitHub Actions logic, such as checking out code, setting up Node.js, running tests, and deploying. This created a maintenance burden and made it difficult to ensure consistency across projects.

To fix this, we adopted **composable building blocks**:

- Reusable **composite actions**: small, focused units of functionality.
- Reusable **workflow templates**: orchestrate multiple actions into full pipelines.

Now, updates can be made **once**, shared across all projects, and reduce the chance of bugs or drift between implementations.

---

## 📁 Folder Structure

```
.github/actions
├── docker/
│   ├── build-tag-release/
│   │   └── action.yml
│   ├── push-release/
│   │   └── action.yml
│   ├── registry-login/
│   │   └── action.yml
│   ├── remove-image/
│   │   └── action.yml
│   └── tag-image/
│       └── action.yml
├── docs/
│   ├── deploy/
│   │   └── action.yml
│   └── upload/
│       └── action.yml
├── release/
│   ├── create-release/
│   │   └── action.yml
│   ├── set-release-tag/
│   │   └── action.yml
│   └── upload-release/
│       └── action.yml
└── setup/
    ├── cache/
    │   └── action.yml
    ├── checkout/
    │   └── action.yml
    ├── create-token/
    │   └── action.yml
    ├── env/
    │   └── action.yml
    ├── node/
    │   └── action.yml
    └── ruby/
        └── action.yml

.github/workflows
├── add_to_tech_debt_project_reusable.yml
├── check-release-version.yml
├── create-release-pr.yml
└── generate_issue_number.yml
```

### `.github/actions/` — Composite Actions

This folder contains **reusable action steps** defined as [composite actions](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action).

Each subfolder defines one composite action, with its own `action.yml`.

These actions are designed to encapsulate specific, repeatable sequences such as:

- `setup-node`: Setup Node.js and install dependencies.
- `docker-login`: Authenticate to GitHub Container Registry.

You can mix and match these within any workflow.

---

### `.github/workflows/` — Reusable Workflows

This folder contains **workflow templates** that can be [called from other workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows).

They represent higher-level automation patterns like:

- `check-release-version.yml`: A workflow to check if the release version has changed between pull requests into master.
- `add_to_tech_debt_project_reusable.yml`: Adding a pull request to the technical debt board.

These workflows are reusable via the `workflow_call` trigger, and can be invoked from other repositories to ensure consistency.

---

## 🚀 How to Use

### 1. Reusing a Composite Action

To use a composite action defined in the `.github/actions` folder in the `.github` repository:

```yaml
jobs:
  some-tests:
    runs-on: ubuntu-latest
    steps:
      - name: Setup stable Chrome
        uses: sanger/.github/.github/actions/tests/setup-chrome@master
        with:
          chrome-version: 128
          install-chromedriver: true
          install-dependencies: true
```

---

### 2. Calling a Reusable Workflow

If you want to call a reusable workflow defined in the `.github` repository:

```yaml
name: Create Release

on:
  push:
    branches:
      - develop
jobs:
  pull_request:
    uses: sanger/.github/.github/workflows/create-release-pr.yml@master
```

You can pass inputs and secrets as required by the reusable workflow. Composite steps **DO NOT** have access to environment variables or secrets.

---

## 🧪 Testing New Actions & Workflows

Incomplete

---

## 🔒 Secrets & Permissions

All workflows should define clear boundaries on which secrets and permissions are required. Avoid unnecessary `write` permissions or global access to organisation secrets unless absolutely necessary. PATs (personal access tokens) should be phased out due to potential security risks.

Across our actions, we use GitHub application installation tokens which are generated per job. If these can't be used, PATs should be used if appropriate. Currently, the action that removes old Docker images is the only place we still use PATs.

---

## ✅ Best Practices

- Keep composite actions **single-purpose** and **small**.
- Avoid hard-coding values inside workflows by using `inputs` and `secrets`.
- Use **clear and descriptive names** for actions and workflows to improve readability and discoverability.
- Document each composite action and reusable workflow with a comment explaining usage, inputs, and examples.
- Use **consistent naming conventions** (e.g., kebab-case for folder names).
- Keep **secrets scoped appropriately** (environment or org-level) and declare them explicitly in workflows.
- Use the `concurrency` key in workflows to avoid overlapping runs where appropriate.
- Run actions locally or in sandbox/test repositories before introducing them into production workflows.

---

## 📚 Resources

- [GitHub Docs: Reusable Workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows)
- [GitHub Docs: Composite Actions](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action)
- [GitHub Docs: Security Best Practices](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)

---

## 🙌 Final Notes

By adopting this modular and reusable GitHub Actions approach, the team benefits from:

- ⚡ Faster development and deployment setup.
- 🛠️ Easier debugging and consistency across repositories.
- 🔁 Reusability and centralised updates.
