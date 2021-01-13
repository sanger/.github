# Standards for development within PSD

## Table of contents

<!-- toc -->

- [Releases](#releases)
- [IDE extentions](#ide-extentions)
  * [Visual Studio Code](#visual-studio-code)
  * [Miscellaneous](#miscellaneous)
    + [EditorConfig](#editorconfig)
      - [Python](#python)
      - [Ruby](#ruby)

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

## IDE extentions

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
