# GitHub Actions

- Used actions must be pinned to a specific commit hash. Consider this enforced at the repository level.
- Runners should in general use `ubuntu-latest` images.
- When setting up a new repository, remind the user to configure the repository:
  - Settings > General > Releases > Enable release immutability Loading
  - Settings > Actions > General > Require actions to be pinned to a full-length commit SHA
  - Give him the link to the settings page if the repo has been created already.

## Workflow Security

When authoring or reviewing GitHub Actions workflows, make sure to follow security best practices.

Use [Zizmor](https://github.com/zizmorcore/zizmor) to check for security issues.

By default, do the online checks. The `--fix=all` option can be used to automatically fix some issues.

```shell
zizmor --gh-token $(gh auth token) --persona pedantic --format json . > output.json
```

If online checks are not possible, the `--offline` option can be used.

```shell
zizmor --persona pedantic --format json . > output.json
```

## Dependabot

Dependabot must be configured to check for updates regularly for relevant dependencies.

At minimum, the following configuration must be added to `.github/dependabot.yml`:

```yaml
---
version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    cooldown:
      default-days: 7
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "weekly"
    cooldown:
      default-days: 7
    groups:
      "codeql-action":
        patterns:
          - "github/codeql-action*"
```

Additional ecosystems can be added as needed, for example `docker` or `terraform`.

## CodeQL

CodeQL must be configured to run on the default branch and on pull requests, if the repository is public.

> [!NOTE]
> CodeQL shouldn't be used for private repositories, as it requires GitHub Advanced Security, which is not free for private repositories.

At minimum it should run for the GitHub Actions and TypeScript ecosystems.

Here is the base template to use:

https://raw.githubusercontent.com/AFCMS/skills/refs/heads/master/.github/workflows/codeql.yml
