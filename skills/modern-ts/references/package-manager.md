# PNPM package management

[PNPM](https://pnpm.io) is the package manager to use.

## Supply chain

`pnpm-workspace.yaml` must be created at the root of the repository.

```yaml
---
blockExoticSubdeps: true
minimumReleaseAge: 360 # 6 hours
trustPolicy: no-downgrade

pmOnFail: ignore
```
