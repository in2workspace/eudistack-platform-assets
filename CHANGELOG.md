# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [Unreleased]

### Added

- **Issuance UI policy** — `tenants/issuance-ui.json`, a single document declaring which
  credentials the Issuer UI (`eudistack-mfe-credential-manager`) offers a form for, per
  tenant. It narrows what the issuer already allows: everything a tenant's
  `tenant_credential_profile` enables stays issuable through the API, while some credentials
  are meant to be issued through the API only.
  - Entries are lineages — `<type>.<format-family>`, a configuration id **without** its
    trailing version (`learcredential.employee.w3c`). The format is part of what is allowed,
    so a credential can be offered in one format and withheld in another. The version is
    chosen by the UI, which always offers the newest the issuer declares.
  - `default` applies to every tenant with no entry under `tenants`; a per-tenant entry
    replaces it entirely (it does not merge). An entry of `[]` is a valid policy meaning
    "this tenant issues only through the API".
  - The UI is **fail-closed**: if this document is unreachable or malformed, no credential
    can be issued from the UI and the screen says the catalogue is unavailable. Treat it as
    production configuration — a typo in a lineage silently removes it from the form.
  - The initial contents reproduce the restrictions the UI applied from hardcoded lists
    before this document existed: the LEAR Machine credential is reserved to `dome` plus the
    two operator tenants (`sandbox`, `platform`), and every other tenant is offered the LEAR
    Employee credential only. Doctor ID (`cgcom`) and the Gaia-X Label credential (`dome`)
    were restricted the same way, but they have no issuance form in the UI at all, so they
    are not listed here — this document says what the UI OFFERS, not what a tenant may issue.

## [1.0.1] - 2026-07-02

### Added

- **DOME embedded footer** — `footerEmbedCode` added to `tenants/dome/theme.json`.
- **Tenant URLs** — `supportUrl` added across all tenants; wallet / custom-domain URLs updated.

### Changed

- **DOME colors** — updated secondary and auth background/gradient colors.

## [1.0.0] - 2026-03-24

### Added

- **Multi-tenant asset system** — Per-tenant directories under `tenants/` with
  branding assets (logo, favicon, theme.json) for each organization
- **Altia tenant** — Logo (SVG, dark variant), favicon, and theme configuration
- **DOME tenant** — Logo (PNG), issuer logo, favicon, and theme configuration
- **CGCOM tenant** — Logo, favicon, and theme configuration
- **RFEF tenant** — Logo and favicon
- **ISBE tenant** — Logo (SVG) and favicon (SVG)
- **Legacy tenant directories** — Top-level `Altia/`, `DOME/`, `ISBE/`, `OMC/`,
  `RFEF/` preserved for backward compatibility during migration

[Unreleased]: https://github.com/in2workspace/eudistack-platform-assets/compare/v1.0.1...HEAD
[1.0.1]: https://github.com/in2workspace/eudistack-platform-assets/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/in2workspace/eudistack-platform-assets/releases/tag/v1.0.0
