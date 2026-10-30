# Git

## Branches

- The default branch must be `master`.
- If a newly created repository doesn't have a `master` branch, it should be renamed to `master`.

## .gitignore

Use the following Toptal template for `.gitignore` files, add project-specific entries at the end of the file.

https://www.toptal.com/developers/gitignore/api/node,linux,macos,windows,visualstudiocode

## Linguist overrides

- If the repositories contain generated files, like bundled JavaScript, you should configure overrides for GitHub's linguist to avoid misleading language statistics.
- Similarly, it might be needed to force the detection of certain files like Markdown if they represent the main content of the repository.
- If assets of specific types are not properly detected, you can also add overrides for them.

- Linguist overrides reference: https://raw.githubusercontent.com/github-linguist/linguist/refs/heads/main/docs/overrides.md
- GitHub supported languages: https://raw.githubusercontent.com/github-linguist/linguist/refs/heads/main/lib/linguist/languages.yml
