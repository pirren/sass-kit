# Releasing

Personal notes for cutting a dashcss release — the "how I ship it" checklist,
not public docs.

## Versioning model

- Releases are **git tags** (`vX.Y.Z`) created by `npm version`. Tags are
  immutable, so a project pinned to a tag stays reproducible forever — no need
  to keep old versions alive as branches.
- Develop on `main`; tag when ready to release.
- SemVer `MAJOR.MINOR.PATCH` — breaking / feature / fix.

## Cut a release

```sh
# 1. main is clean and the build is current
npm run sass:build
git add -A && git commit -m "…"          # if anything needs committing

# 2. move CHANGELOG [Unreleased] items under the new version heading

# 3. bump version + create the vX.Y.Z tag (updates package.json, commits, tags)
npm version patch                        # or: minor | major

# 4. push commits AND the tag
git push origin main --follow-tags
```

## Pre-releases (RC / beta)

```sh
npm version prerelease --preid=rc        # 0.1.0 -> 0.1.1-rc.0
npm version prerelease                   # -> 0.1.1-rc.1
```

Consuming projects only pick these up if they explicitly pin the pre-release
tag.

## How other projects pin it

```jsonc
// package.json in a consuming project
"dependencies": {
  "dashcss": "github:pirren/dashcss#v0.1.0"    // pin a tag (recommended)
  // "dashcss": "github:pirren/dashcss#main"   // always-latest (riskier)
}
```

Update a consumer with `npm update dashcss`, or bump the pinned tag.

## Pre-tag checklist

- [ ] `npm run sass:build` clean; `dist/` current if committed
- [ ] `CHANGELOG.md` updated for this version (+ date)
- [ ] version bump is the right SemVer step
- [ ] `git push origin main --follow-tags`
