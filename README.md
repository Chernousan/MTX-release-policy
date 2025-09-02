# Code version

A Python project with automated semantic versioning using GitHub Actions and GitFlow methodology.

## Features

- Automated semantic versioning
- GitHub Actions for CI/CD
- Version management through tags

## Version Management

This project uses semantic versioning (SemVer) with the format: `MAJOR.MINOR.PATCH[-RELEASE.BUILD]`

- **MAJOR**: Incremented for incompatible API changes
- **MINOR**: Incremented for backward-compatible functionality additions
- **PATCH**: Incremented for backward-compatible bug fixes
- **RELEASE**: Pre-release identifier (alpha, beta, rc) or "release" for stable versions
- **BUILD**: Build number for pre-releases

### Current Version

The current version is dynamically managed in `settings.py` and can be displayed by running:

```python
python main.py
```

## GitFlow Methodology

This project follows the GitFlow branching model:

### Branch Structure

- **main**: Production-ready code with stable releases
- **develop**: Integration branch for features
- **feature/***: New feature development
- **release/***: Release preparation
- **hotfix/***: Critical bug fixes for production

### Workflow

1. **Feature Development**:
   ```bash
   git checkout develop
   git checkout -b feature/new-feature
   # Make changes
   git checkout develop
   git merge --no-ff feature/new-feature
   ```

2. **Release Process**:
   ```bash
   git checkout develop
   git checkout -b release/1.2.0
   # Update version in settings.py
   # Final testing and bug fixes
   git checkout main
   git merge --no-ff release/1.2.0
   git tag -a v1.2.0 -m "Release version 1.2.0"
   git checkout develop
   git merge --no-ff main
   ```

3. **Hotfix Process**:
   ```bash
   git checkout main
   git checkout -b hotfix/1.2.1
   # Fix critical issue and update version
   git checkout main
   git merge --no-ff hotfix/1.2.1
   git tag -a v1.2.1 -m "Hotfix version 1.2.1"
   git checkout develop
   git merge --no-ff main
   ```

## Automated Version Management

### GitHub Actions Workflows

#### 1. Version Management Workflow

**Triggers:**
- Push tags matching `v*.*.*` pattern

**Automatic Tag Processing:**
When you push a tag like `v1.2.3`, the workflow automatically:
- Extracts version components
- Updates `settings.py`
- Commits changes back to the repository


## Installation

```bash
# Clone the repository
git clone https://github.com/Chernousan/workflow-exp.git
cd workflow-exp
```

## Usage

```bash
# Run the main application
python main.py
```

## License

This project is licensed under the Apache Version 2.0  - see the [LICENSE](LICENSE) file for details.

## GitHub Actions Setup

### Required Secrets

No additional secrets are required beyond the default `GITHUB_TOKEN`.


## Ref
Semantic Versioning: https://semver.org/

GitFlow simple explanation: https://www.youtube.com/watch?v=Aa8RpP0sf-Y