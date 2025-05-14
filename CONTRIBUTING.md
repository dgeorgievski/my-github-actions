# Contributing to `platform-github-actions`

Welcome to the centralized GitHub Actions library for our organization! This repository contains **reusable workflows** designed to standardize and simplify CI/CD pipelines across services and languages.

We value clean, consistent, and scalable automation—thank you for helping us improve it.

---

## What Belongs Here

This repo contains:

- Reusable workflows for common CI/CD tasks (e.g., linting, testing, building)
- Language or platform-specific variants (Node.js, Python, Java, etc.)
- Utility workflows (e.g., container publishing, deployment)
- Templates to help service teams onboard quickly

---

## Repository Structure

```text
.github/workflows/     # Reusable workflows (marked with `workflow_call`)
templates/             # Example workflows for consuming teams
README.md              # Overview and usage examples
CONTRIBUTING.md        # This file
```

## Workflow Requirements

All workflows must:

1. Use on: workflow_call so they are reusable.
2. Accept appropriate inputs with:

    - Clear naming
    - Default values where reasonable
    - Descriptions (via README or inline comments)
3. Follow our naming conventions:
    - `test-node.yml`, `lint-python.yml`, `build-java.yml`, etc.
4. Include internal comments explaining any non-trivial logic.
5. Avoid hardcoding secrets — use secrets input parameters.

## Getting Started

1. Create a feature branch

    ```bash
    git checkout -b feat/test-python-py310
    ```

2. Make your changes
3. Test your workflow:
    - Push to a sandbox repo that consumes the workflow.
    - Or use act to simulate it locally (optional).
4. Commit using Conventional Commits:

    ```bash
    git commit -m "feat(python): add test-python workflow with version input"
    ```

5. Open a PR to main and request review

## Review Checklist

- Uses workflow_call
- Follows naming conventions and folder structure
- Inputs are documented, typed, and have sensible defaults
- Steps are well-commented
- No hardcoded secrets or org-specific values
- Reusable across teams/projects

## Linting and Validation

Before pushing:

```bash
yamllint .github/workflows/
```

## Security Guidelines

- No secrets in code. Use:
- secrets.MY_SECRET as input
- GitHub Environments or repo-level secrets
- Avoid referencing privileged infrastructure in reusable workflows

## Collaboration & Support

Need help? Ping us in the #platform-github-actions channel on Slack, or tag a CODEOWNER in your PR.

Let’s make CI/CD fast, safe, and delightful—for everyone.

Thanks for contributing!!!
