# Standards for development within PSD

## Table of contents

<!-- toc -->

- [Releases](#releases)
- [IDE extensions](#ide-extensions)
  * [Visual Studio Code](#visual-studio-code)
  * [Miscellaneous](#miscellaneous)
    + [EditorConfig](#editorconfig)
      - [Python](#python)
      - [Ruby](#ruby)
- [Dependency guidelines](#dependency-guidelines)

<!-- tocstop -->

## Releases

[Semantic Versioning](https://semver.org/) (semver) should be used as far as possible:
> Given a version number MAJOR.MINOR.PATCH, increment the:
>
> 1. MAJOR version when you make incompatible API changes,
> 1. MINOR version when you add functionality in a backwards compatible manner, and
> 1. PATCH version when you make backwards compatible bug fixes.
>
> Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

Prepend the release with the "release-" or "v":

* `release-1.2.3`
* `v1.2.3`

## Security

### Client-side

We use Talisman via [Global Git Hooks](https://github.com/sanger/global-git-hooks) to try to prevent sensitive information being committed to our repositories. Follow the setup steps in the Readme to get it working on your machine.

## IDE extensions

It is useful (but not required) when the same linting and/or formatting extensions are used between developers, here
are some examples:

### Visual Studio Code

* [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
* [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)

### Miscellaneous

#### EditorConfig

[EditorConfig](https://EditorConfig.org) can help keep code formats similar accross developers' IDEs.

Config to store in `.editorconfig`:

##### Python

```
# EditorConfig is awesome: https://EditorConfig.org

# top-most EditorConfig file
root = true

[*]
indent_style = space
indent_size = 4
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

##### Ruby

```
# EditorConfig is awesome: https://EditorConfig.org

# top-most EditorConfig file
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

## Dependency guidelines

To ensure our repositories are using up-to-date libraries and that any security vulnerabilities are patched quickly, we use Depfu and Dependabot to manage our code dependencies. These systems automatically open pull requests to bump dependency versions which contain information about the changes as well as running against the CI. In order to ensure we make the most out of this process there are guidelines we follow:

1. Auto merge security requests and patch updates (in semver major.minor.**patch**) if they are passing CI builds.
2. Review minor / major updates (in semver **major**.**minor**.patch) for breaking changes, deprecation warnings, and new features. Pull down the changes and manually check for issues locally, even if passing CI.
3. Wait 1-2 weeks before merging in a new non-security related dependency update. This prevents having to re-merge a dependency multiple times for any hotfixes or additional patches they put out in that time.
4. Split out major breaking changes if they require their own story. This may include major framework updates like Rails, Vue, Flask.
5. Deploy dependencies all the way to production. Check for existing work in progress to ensure you don’t disrupt or break in-progress work. This is to ensure that apps are regularly updated with security updates and the deployment pipelines are still functioning.
