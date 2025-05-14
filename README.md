# Platform GitHub Actions Library `platform-github-actions`

This repository contains **reusable GitHub Actions workflows** that standardize CI/CD pipelines across our organization. These workflows are centrally maintained by the Platform Engineering team and are meant to be consumed via `workflow_call` from individual service repositories.

## What’s Included

| Workflow Name       | Purpose                         | Language / Use Case   |
|---------------------|---------------------------------|-----------------------|
| `test-node.yml`     | Run tests for Node.js services  | Node.js (npm, yarn)   |
| `lint-python.yml`   | Lint Python code with flake8    | Python                |
| `build-java.yml`    | Build and test Java projects    | Java / Maven / Gradle |
| `deploy.yml`        | Deploy to environment/stage     | Any (requires setup)  |
| ...                 | ...                             | ...                   |
|                     |                                 |                       |

## How to Use a Reusable Workflow

From your service repository, create a workflow like this:

```yaml
# .github/workflows/ci.yml
name: CI Pipeline

on:
  push:
    branches: [ main ]

jobs:
  test:
    uses: your-org/platform-github-actions/.github/workflows/test-node.yml@v1
    with:
      node-version: '20'
```

## Available Inputs

Inputs vary by workflow. Refer to the top of each workflow YAML file or [input reference section](#workflow-inputs).

🧪 Examples

We provide starter templates in the /templates folder:

- sample-node.yml
- sample-python.yml

Copy and customize one for your service to get started quickly.

⸻

🚦 Versioning

Workflows should be consumed using tagged versions, not main.

✅ Recommended:

```yaml
uses: your-org/platform-github-actions/.github/workflows/test-node.yml@v1
```

❌ Avoid:

```yaml
uses: your-org/platform-github-actions/.github/workflows/test-node.yml@main
```

## Contributing

Want to add a new workflow or improve an existing one?

See CONTRIBUTING.md for:

- Naming conventions
- Coding standards
- Testing tips
- Review checklist

## Support

- Slack: #platform-github-actions
- GitHub Issues: Open an issue
- Maintainers: @platform-dev1, @platform-dev2

## Security

- Secrets must be passed via secrets input or GitHub Environments
- No hardcoded credentials or tokens
- No direct org resource references unless templated

## Workflow Inputs

Below are common inputs for popular workflows:

### test-node.yml

| Input        | Type   | Default | Description            |
|--------------|--------|---------|------------------------|
| node-version | string | '18'    | Node.js version to use |

### test-python.yml

| Input          | Type   | Default | Description           |
|----------------|--------|---------|-----------------------|
| python-version | string | '3.11'  | Python version to use |
