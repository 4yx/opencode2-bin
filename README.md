# opencode2-bin

AUR package repo for `opencode2-bin` (originally [bermudi/aur-packages](https://github.com/bermudi/aur-packages/tree/9e323b556e17d1f0d5df2877d7c402e34b80933c)). 
The repo root is the package directory, and is the source of truth for its `PKGBUILD`, `.SRCINFO`, and auxiliary files.
GitHub Actions keep the AUR in sync.

## Layout

```
PKGBUILD              # package definition (repo root = package dir)
.SRCINFO              # generated from PKGBUILD
.github/
  scripts/
    update-pkgbuild.sh    # rewrite pkgver + checksums; reset pkgrel on version bumps
    generate-srcinfo.sh   # source PKGBUILD -> .SRCINFO (no makepkg needed)
  workflows/
    opencode2-bin.yml     # per-package: poll upstream, call update-aur
    update-aur.yml        # reusable: bump, commit, tag, release, push to AUR
```

## Packages

| Directory | AUR package                         | Upstream channel                        |
|-----------|-------------------------------------|-----------------------------------------|
| `.`       | `opencode2-bin` (currently defunct) | opencode v2 npm binaries (`latest` tag) |

## Secrets

- `AUR_SSH_PRIVATE_KEY` — SSH private key authorized on your AUR account.
  Required for the AUR push step; without it the workflow updates GitHub only.
