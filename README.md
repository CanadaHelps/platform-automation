# Platform Automation

Reusable GitHub Actions workflows for the CanadaHelps platform.

## Overview

This repository hosts a curated set of reusable GitHub Actions workflows for building, testing, releasing, and deploying applications across the CanadaHelps organization.

## Reusable Workflows

### dotnet-ci.yml
- **Purpose:** .NET build, test, and code quality checks
- **Usage:** `uses: CanadaHelps/platform-automation/.github/workflows/dotnet-ci.yml@v1`
- **Inputs:** Project paths, .NET version, test filters

### docker-build.yml
- **Purpose:** Build and push Docker images to Azure Container Registry
- **Usage:** `uses: CanadaHelps/platform-automation/.github/workflows/docker-build.yml@v1`
- **Inputs:** Docker image name, registry, tags

### publish-nuget.yml
- **Purpose:** Build and publish NuGet packages
- **Usage:** `uses: CanadaHelps/platform-automation/.github/workflows/publish-nuget.yml@v1`
- **Inputs:** Project path, .NET version, version suffix, auth token

### release.yml
- **Purpose:** Create semantic version tags and GitHub Releases
- **Usage:** `uses: CanadaHelps/platform-automation/.github/workflows/release.yml@v1`
- **Inputs:** Version, release notes

### apply-rulesets.yml
- **Purpose:** Apply branch protection and repository rulesets
- **Usage:** `uses: CanadaHelps/platform-automation/.github/workflows/apply-rulesets.yml@v1`
- **Inputs:** Ruleset directory, dry-run flag

### azure-deploy.yml
- **Purpose:** Deploy applications to Azure environments
- **Usage:** `uses: CanadaHelps/platform-automation/.github/workflows/azure-deploy.yml@v1`
- **Inputs:** Environment, image tag, app name

## Usage

Reference workflows using SHA-pinned commits for safety:

```yaml
jobs:
  build:
    uses: CanadaHelps/platform-automation/.github/workflows/dotnet-ci.yml@<SHA>
    with:
      project-path: 'MyProject/'
      dotnet-version: '8.0.x'
```

## Guidelines

1. **Security:** Always pin to a specific commit SHA, not a branch
2. **Access Control:** Only org owners and designated maintainers can modify workflows
3. **Testing:** Test workflow changes in a feature branch before merging to main
4. **Documentation:** Update this README when adding or modifying workflows

## Requirements

- GitHub Actions enabled
- Appropriate secrets configured in calling repositories
- For Azure operations: OIDC authentication configured

