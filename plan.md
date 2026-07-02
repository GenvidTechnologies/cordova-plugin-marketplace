# Plan: Migrate namespace `@genvid` → `@genvidtech`, org → GenvidTechnologies

## Branch
`chore/rename-namespace-genvidtech`

## Summary
Mechanical rename across three groups. The npm scope moves from `@genvid` to
`@genvidtech` (the new scope is already provisioned on npm with OIDC trusted
publishing), the GitHub org moves from `genvid-holdings` to `GenvidTechnologies`
(the repo has already been transferred), and the shared reusable-workflow repo
`genvid-holdings/genvid-public-ci` is now `GenvidTechnologies/github-actions-public`
(internal path `.github/workflows/node-gate.yml@main` unchanged — confirmed with user).

## Rename groups

### A. npm scope `@genvid` → `@genvidtech`
- `package.json` — `name` and `cordova.id`
- `package-lock.json` — root `name` (2 occurrences)
- `plugin.xml` — `id="…"`
- `README.md` — install command, scope link (text + npmjs URL), and the
  `npm pack` tarball name `genvid-…tgz` → `genvidtech-…tgz`

### B. GitHub org `genvid-holdings` → `GenvidTechnologies`
- `package.json` — `repository.url`, `bugs`
- `plugin.xml` — `<repo>`, `<issue>`
- `types/index.d.ts` — `// Project:` URL

### C. Reusable-workflow repo → `GenvidTechnologies/github-actions-public`
- `.github/workflows/ci.yml` and `publish.yml` `uses:` →
  `GenvidTechnologies/github-actions-public/.github/workflows/node-gate.yml@main`

### D. Project doc
- `CLAUDE.md` — scope and org references updated for accuracy.

## Out of scope (deliberate)
- `.vscode/settings.json` — stale CircleCI/Bitbucket local editor setting (already
  `genvidtech`); CircleCI removed. Left as-is.
- `plugin.xml` version `1.1.0` vs `package.json` `1.1.1` — pre-existing mismatch,
  unrelated to this rename.
- Native package `com.genvidtech.*` — already `genvidtech`; unchanged.
- **No version bump / no release.** This PR only renames. The package first
  *publishes* under `@genvidtech` on the next `vX.Y.Z` tag (follow-up).
- Auto-memories referencing the old scope/org are updated separately (outside repo).

## No ADR
Pure mechanical rename — no architectural decision or rejected alternative. ADR
threshold not met.

---

## Tasks (each = one commit)

### Task 1 — Rename scope + org across package/plugin metadata & docs — ts-implementer
Groups A, B, D: `package.json`, `package-lock.json`, `plugin.xml`, `types/index.d.ts`,
`README.md`, `CLAUDE.md`.

**Commit:** `Move npm scope to @genvidtech and repo URLs to GenvidTechnologies`

### Task 2 — Point CI workflows at the renamed reusable-workflow repo — ts-implementer
Group C: `.github/workflows/ci.yml`, `.github/workflows/publish.yml`.

**Commit:** `Point CI workflows at GenvidTechnologies/github-actions-public`

---

## Gate (per task, before commit)
- `npm run lint` + `npm run typecheck`.
- Task 1 end-to-end verify: `npm pack --dry-run` confirms the tarball name becomes
  `genvidtech-cordova-plugin-marketplace-1.1.1.tgz` (proves the scope rename took).
- `genvid-dev:code-reviewer` at the end.

## Risks
- Wrong reusable-workflow path silently breaks CI on the next PR/tag — mitigated by
  confirming the exact `uses:` value with the user.
- `package-lock.json` edited directly (no scope-dependent deps); `npm ci` should still
  resolve — verified by lint running off the installed tree.
