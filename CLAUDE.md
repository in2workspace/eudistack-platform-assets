# Platform Assets — Repo Guide for Claude

> **Per-repo CLAUDE.md.** Loaded only when working inside this repo. The
> SDD Constitution lives in `../eudistack-platform-dev/CLAUDE.md`.

## Identity

Shared assets for the EUDIStack platform: branding (logos, colours,
fonts), credential schemas, public well-known files, sample data.

**Read-only for most contributors.** Updates require PM/Design review.

## Layout

```text
branding/        ← Logos, brand guidelines, colour palettes
schemas/         ← Credential JSON Schemas (SD-JWT VC vct definitions)
well-known/      ← Files for /.well-known/* endpoints (jwks, openid-credential-issuer, etc.)
samples/         ← Sample credentials, test data
```

## Common commands

| Task | Command |
|------|---------|
| Validate JSON Schemas | `npx ajv compile -s 'schemas/**/*.json'` (if Node tooling available) |
| Lint Markdown | `npx markdownlint '**/*.md'` |

## Conventions

- Image assets: SVG preferred; PNG fallbacks at 1x/2x/3x.
- JSON Schemas: draft-07 or 2020-12; declare `$id` as a URL.
- `vct` URIs in SD-JWT VC schemas MUST be HTTPS-resolvable.
- No PII in `samples/` — use synthetic data only.

## Git workflow

- **Squash merge to `main`.** Conventional Commits.

## References

- Constitution: [`../eudistack-platform-dev/CLAUDE.md`](../eudistack-platform-dev/CLAUDE.md)
- SAD: [`../eudistack-platform-dev/docs/_shared/architecture/sad.md`](../eudistack-platform-dev/docs/_shared/architecture/sad.md)
