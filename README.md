# Governance Migration Demo

This repository demonstrates how to use Lineage's reusable workflows to migrate existing governance repositories to Lineage baseline format.

## Overview

This demo repository contains example workflows that show how to test migration compatibility and perform actual migration to generate a Lineage baseline with different output modes including artifacts, commits and pull requests.

This repository doesn't contain sample governance files. Instead, the workflows analyze external governance repositories specified by URL.

## Workflow Usage

### Test Migration Compatibility

The `.github/workflows/test-migration.yml` workflow tests whether a governance repository is ready for migration. Run the "Test Governance Migration Compatibility" workflow from the Actions tab, provide the governance repository URL, and review analysis results in the workflow logs.

This workflow analyzes repository structure and governance files, detects project languages and ecosystems, validates migration compatibility, and provides recommendations for any issues found.

### Migrate Governance Repository

The `.github/workflows/migrate-to-lineage.yml` workflow performs actual migration to create Lineage baseline. Run the "Migrate Governance Repository to Lineage" workflow from the Actions tab, provide governance repository URL and organization details, then choose an output mode.

Output modes:
- **artifact**: Downloads a ZIP with generated baseline
- **commit**: Commits baseline directly to this repository
- **pr**: Creates a pull request with baseline changes

The migration generates a complete Lineage baseline with organization-specific configuration, policy packs for all detected governance files, `.lineage.toml` configuration file and migration report with next steps.

## Testing with Governance Repositories

You can test the workflows with any governance repository that contains standard files:
- LICENSE
- SECURITY.md
- CODEOWNERS / .github/CODEOWNERS
- .editorconfig
- .pre-commit-config.yaml
- .github/dependabot.yml

## Migration Process

1. Run the test workflow to check compatibility and fix any issues
2. Run the migrate workflow with your desired output mode
3. Use the generated baseline to create your organization's Lineage baseline repository

After successful migration, create your organization's baseline repository using the generated files, customize the baseline for your specific needs and deploy to consumer repositories using Lineage's consumption patterns.