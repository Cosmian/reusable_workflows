# GitHub Copilot Instructions for Cosmian Reusable Workflows

## Repository Overview

This repository contains a comprehensive collection of reusable GitHub Actions workflows for Cosmian's projects. It provides standardized CI/CD pipelines for building, testing, linting, and publishing Rust projects, containerized applications, and multi-language packages.

## Repository Structure

```
.github/workflows/          # Reusable workflow definitions
├── build_*.yml            # Build workflows for different platforms/contexts
├── cargo-*.yml             # Rust/Cargo specific workflows
├── cloudproof*.yml         # Cloudproof project workflows
├── ndk.yml                 # Android NDK builds
└── package-*.yml           # Package publishing workflows
```

## Key Workflow Categories

### Build Workflows
- `build_all.yml` - Orchestrates builds across multiple platforms
- `build_generic.yml` - Generic build workflow for standard projects
- `build_in_container.yml` - Containerized builds (Rocky Linux)
- `build_windows.yml` - Windows-specific builds
- `build_docker_image.yml` - Docker image building

### Cargo/Rust Workflows
- `cargo.yml` - Core Rust compilation workflow
- `cargo-lint.yml` - Linting and testing with services (Redis, PostgreSQL)
- `cargo-audit.yml` - Security auditing
- `cargo-bench.yml` - Performance benchmarking
- `cargo-doc.yml` - Documentation generation
- `cargo-fmt.yml` - Code formatting
- `cargo-machete.yml` - Dead code detection
- `cargo-publish.yml` / `cargo-publish-workspace.yml` - Crate publishing
- `cargo-semver.yml` - Semantic versioning checks
- `clippy.yml` - Rust linting

### Cloudproof Workflows
- `cloudproof.yml` - Main Cloudproof build orchestration
- `cloudproof_flutter.yml` / `cloudproof_flutter_darwin.yml` - Flutter builds
- `cloudproof_java.yml` - Java package builds
- `cloudproof_js.yml` / `cloudproof_kms_js.yml` - JavaScript builds
- `cloudproof_python.yml` - Python package builds

### Publishing & Distribution
- `package-cosmian-com.yml` - Publishing to package.cosmian.com
- `push-artifacts.yml` - Artifact distribution

## Workflow Input Patterns

Most workflows follow these common input patterns:

### Required Inputs
- `toolchain`: Rust toolchain version (e.g., "stable", "nightly-2025-03-31")
- `target`: Build target (e.g., "x86_64-unknown-linux-gnu")
- `os`: Runner OS (e.g., "ubuntu-22.04", "windows-latest")

### Optional Inputs
- `exclusions`: Package exclusions for testing
- `pre-requisites`: System dependencies to install
- `artifacts`: Build artifacts to collect
- `debug_artifacts`: Debug build artifacts
- `features`: Feature flags for builds

## Development Guidelines

### When Creating New Workflows

1. **Use consistent input naming**: Follow existing patterns for `toolchain`, `target`, `os`
2. **Add proper documentation**: Include clear descriptions in workflow files
3. **Support exclusions**: Most workflows should support package exclusions
4. **Use matrix builds**: For multi-platform support
5. **Inherit secrets**: Use `secrets: inherit` for reusable workflows
6. **Add service dependencies**: Include Redis/PostgreSQL services when needed for tests

### Workflow File Structure
```yaml
---
name: Descriptive Workflow Name

on:
  workflow_call:
    inputs:
      # Define required and optional inputs
      toolchain:
        required: true
        type: string
      # ... other inputs

jobs:
  job-name:
    runs-on: ${{ inputs.os }}
    # Add service dependencies if needed
    services:
      postgres: # PostgreSQL service config
      redis: # Redis service config
    
    steps:
      # Implementation steps
```

### Testing Workflows

- Workflows are validated using pre-commit hooks with `check-github-workflows`
- Test changes in a fork before merging
- Verify matrix builds work across all specified platforms
- Check that artifact collection works correctly

### Code Quality Standards

The repository uses extensive pre-commit hooks including:
- **YAML formatting**: yamlfmt with specific indentation rules
- **Markdown linting**: markdownlint with customized rules
- **Security checks**: typos, private key detection
- **JSON Schema validation**: GitHub Actions schema validation
- **Shell scripting**: shellcheck for shell scripts

### Common Patterns to Follow

1. **Container Builds**: Use Cosmian's standardized container images (cosmian/rockylinux9)
2. **Artifact Naming**: Use descriptive archive names that match the build context
3. **Toolchain Management**: Support both stable and nightly Rust toolchains
4. **Cross-Platform**: Consider Windows, macOS, and Linux compatibility
5. **Feature Flags**: Support FIPS and other conditional compilation features

### When Modifying Existing Workflows

- **Preserve backward compatibility**: Don't break existing input contracts
- **Test thoroughly**: Changes affect multiple dependent repositories
- **Update documentation**: Keep workflow descriptions current
- **Consider dependencies**: Some workflows depend on others (e.g., cloudproof.yml uses multiple sub-workflows)

## Debugging Common Issues

### Build Failures
- Check toolchain compatibility with target platform
- Verify all required pre-requisites are installed
- Ensure artifact paths are correct for the target OS

### Container Issues
- Verify Docker image availability
- Check that container has required build dependencies
- Ensure proper volume mounting for artifacts

### Publishing Problems
- Verify secrets are properly configured
- Check package registry connectivity
- Ensure version constraints are met

## Integration with External Systems

- **package.cosmian.com**: Custom package repository
- **PyPI**: Python package publishing  
- **crates.io**: Rust crate publishing
- **Docker registries**: Container image publishing
- **GitHub Packages**: Artifact storage

When working with this repository, focus on maintaining consistency with existing patterns while ensuring robust, cross-platform compatibility for Cosmian's diverse project ecosystem.