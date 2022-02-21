# `action-autotag` - **Github Action based on [autotag](https://github.com/pantheon-systems/autotag) utlity**

This action automatically increment version tags to a git repo based on commit messages.

Before using action-autotag for the first time create an initial SemVer tag, eg:

`git tag v0.0.0 -m 'initial tag'`

The next version tag is calculated based on the contents of commit message according to these
rules:

- Bump the **major** version by including `[major]` or `#major` in a commit message, eg:

```
[major] breaking change
```

- Bump the **minor** version by including `[minor]` or `#minor` in a commit message, eg:

```
[minor] new feature added
```

- Bump the **patch** version by including `[patch]` or `#patch` in a commit message, eg:

```
[patch] bug fixed
```

If no keywords are specified a **Patch** bump is applied.

## Example Usage

```yaml
name: Create a new tag

on:
  push:
    branches:
      - master
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v2
        - uses: valitydev/action-autotag@v1
```
