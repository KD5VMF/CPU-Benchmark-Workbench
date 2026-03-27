# Changelog

All notable changes to this project should be documented in this file.

The format is based on a simple Keep a Changelog style.

## [Unreleased]
### Added
- Initial public GitHub repository structure
- Project documentation, contribution guide, security policy, issue templates, and workflow template

## [17.0.0] - 2026-03-27
### Fixed
- Repaired `BitOperations.RotateLeft` / `RotateRight` calls to use the expected `uint` overloads in compiler-sensitive paths

### Notes
- This release is intended to be the stable code line after prior compile-compatibility fixes
