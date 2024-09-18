<!-- markdownlint-configure-file { "MD033": false } -->

# Gitlab-Mirror

[![License](https://img.shields.io/github/license/0xTheProDev/gitlab-mirror?style=for-the-badge&label=license)](https://github.com/0xTheProDev/gitlab-mirror/blob/main/LICENSE)
[![Open Issues](https://img.shields.io/github/issues-raw/0xTheProDev/gitlab-mirror?style=for-the-badge)](https://github.com/0xTheProDev/gitlab-mirror/issues)
[![Closed Issues](https://img.shields.io/github/issues-closed-raw/0xTheProDev/gitlab-mirror?style=for-the-badge)](https://github.com/0xTheProDev/gitlab-mirror/issues?q=is%3Aissue+is%3Aclosed)
[![Open Pulls](https://img.shields.io/github/issues-pr-raw/0xTheProDev/gitlab-mirror?style=for-the-badge)](https://github.com/0xTheProDev/gitlab-mirror/pulls)
[![Closed Pulls](https://img.shields.io/github/issues-pr-closed-raw/0xTheProDev/gitlab-mirror?style=for-the-badge)](https://github.com/0xTheProDev/gitlab-mirror/pulls?q=is%3Apr+is%3Aclosed)
[![Contributors](https://img.shields.io/github/contributors/0xTheProDev/gitlab-mirror?style=for-the-badge)](https://github.com/0xTheProDev/gitlab-mirror/graphs/contributors)
[![Activity](https://img.shields.io/github/last-commit/0xTheProDev/gitlab-mirror?style=for-the-badge&label=most%20recent%20activity)](https://github.com/0xTheProDev/gitlab-mirror/pulse)

## Description

Github Action to Push Latest Change to Corresponding GitLab Mirror Repository

## Usage

**Pre-requisite:** Add your GitLab [Access Token](https://docs.gitlab.com/ee/user/project/settings/project_access_tokens.html)_(preferred)_ or Password into your GitHub secrets.

```yaml
---
name: Mirror Repository

on:
  push:
    branches:
      - main

concurrency: ${{ github.workflow }}-${{ github.ref }}

permissions:
  contents: read

jobs:
  gitlab:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          fetch-depth: 0 # This must be set to 0 to avoid shallow cloning.

      - name: Mirror Repository
        uses: 0xTheProDev/gitlab-mirror@v1
        with:
          password: ${{ secrets.GITLAB_PAT }}
          project-id: "github-mirror"
          username: "gitlab"
```

## Reporting a Bug

Head on to [**Discussion**](https://github.com/0xTheProDev/gitlab-mirror/discussions) section to report a bug or to ask for any feature. Feel to add your queries about using this library as well under _Q & A_ section of it. Remember, do not create any Issues by yourself, maintainers of this repository will open one if deemed necessary.

## Changelog

See [CHANGELOG](https://github.com/0xTheProDev/gitlab-mirror/blob/main/.github/CHANGELOG.md) for more details on what has been changed in the latest release.

## Contributing

See [Contributing Guidelines](https://github.com/0xTheProDev/gitlab-mirror/blob/main/.github/CONTRIBUTING.md).

## License

This project is licensed under the terms of the MIT license, see [LICENSE](https://github.com/0xTheProDev/gitlab-mirror/blob/main/LICENSE) for more details.

<a href="https://github.com/0xTheProDev">
  <img src=".github/assets/the-pro-dev-original.png" alt="The Pro Dev" height="120" width="120"/>
</a>
