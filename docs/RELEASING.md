# Releasing

## Release notes source
- GitHub Release notes come from `CHANGELOG.md` for the matching version section (`## X.Y.Z - YYYY-MM-DD`).
- Keep `## Unreleased` at the top (empty is fine).

## Steps
1. Update `CHANGELOG.md`
   - Move entries from `Unreleased` into a new `## X.Y.Z - YYYY-MM-DD` section.
   - Credit contributors (e.g. `thanks @user`).
2. Ensure CI is green on `main`
   - `pnpm lint`
   - `pnpm test`
   - `gh run list --branch main --limit 1`
3. Tag and push
   - `git tag -a vX.Y.Z -m "vX.Y.Z"`
   - `git push origin vX.Y.Z`

## What happens in CI
- `.github/workflows/release.yml` runs GoReleaser on tag push.
- After assets upload, the workflow updates the GitHub Release body using the `CHANGELOG.md` section for `X.Y.Z`.
