<!-- markdownlint-disable MD024 no-duplicate-heading -->

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

**Types of changes**: `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`

## [Unreleased]

### Changed

- `docs/CC-changelog-feature-scan.md`: add `[yyyy-MM-dd]` dates to main sections (changelog-style)

## [0.3.0] - 2026-03-12

### Added

- `docs/ci-execution/CC-sandbox-platforms-landscape.md`: sandbox platforms landscape analysis
- `docs/ci-execution/CC-version-pinning-resilience.md`: version pinning resilience research
- `docs/configuration/CC-bash-mode-analysis.md`: bash mode analysis
- `docs/plugins-ecosystem/CC-web-scraping-plugins-analysis.md`: web scraping plugins analysis
- `docs/CC-changelog-feature-scan.md`: changelog feature scan (v2.1.0-2.1.71)
- `.github/workflows/changelog-monitor.yml`: changelog monitor workflow with comparison script

### Changed

- `docs/ci-execution/CC-remote-access-landscape.md`: updated with new findings
- All 24 docs: added frontmatter dates (`created`, `updated`, `validated_links`)
- All 24 docs: validated links, updated `validated_links: 2026-03-12`
- Docs folders renamed to reflect actual content categories

## [0.2.0] - 2026-03-08

### Added

- `docs/plugins-ecosystem/CC-plugin-packaging-research.md`: Common Pitfalls section

### Changed

- Restructured docs into category directories: `agents-skills/`, `ci-execution/`, `configuration/`, `context-memory/`, `plugins-ecosystem/`

## [0.1.0] - 2026-03-08

### Added

- Initial 18 Claude Code feature analysis documents
- `README.md`: project overview and navigation
- Repository setup (LICENSE, `.gitignore`)
