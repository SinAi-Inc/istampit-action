# Changelog

All notable changes to this Action will be documented here.

## [v1.0.3] - 2025-08-16

### Fixed (parser)

- Resolved remaining YAML parser errors by normalizing literal block indentation.
- Consolidated run block and embedded Python script with consistent indent under `run: |`.

### Notes (v1.0.3)

- Moving tag `v1` will be advanced to this version.

## [v1.0.2] - 2025-08-16

### Fixed

- Corrected malformed `action.yml` (indentation, misplaced outputs).
- Restored proper `author` and `branding` fields.
- Ensured step `id: stamp` exists so outputs resolve.
- Outputs (`receipts`) now reliably written via `$GITHUB_OUTPUT`.

### Notes

- Moving tag `v1` updated to point to this release.

## [v1.0.1] - 2025-08-16

### Changed

- Housekeeping: badges (Marketplace, example workflow, CodeQL, Scorecard).
- Added outputs (`receipts`) and improved README usage section.
- Example workflow now stamps a dummy file and validates receipt.
- Added scheduled upgrade workflow and Dependabot config.

## [v1.0.0] - 2025-08-16

### Added

- Initial release of iStampit Timestamp composite action.

[v1.0.3]: https://github.com/SinAi-Inc/istampit-action/releases/tag/v1.0.3
[v1.0.2]: https://github.com/SinAi-Inc/istampit-action/releases/tag/v1.0.2
[v1.0.1]: https://github.com/SinAi-Inc/istampit-action/releases/tag/v1.0.1
[v1.0.0]: https://github.com/SinAi-Inc/istampit-action/releases/tag/v1.0.0
