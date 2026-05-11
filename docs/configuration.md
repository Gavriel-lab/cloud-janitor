# Configuration

Cloud Janitor uses configuration to determine which cloud resources to inspect, create, update, or clean up.

## Configuration sources

The project follows Quarkus and SmallRye Config conventions. Settings can be supplied through:

- Environment variables
- YAML configuration
- Runtime properties
- Container or GitHub Action inputs

The repository includes examples in the `config/` directory. Rename or copy a configuration file to `application.yaml` when you want it to be used as the default local configuration.

## Cloud credentials

Cloud Janitor runs operations against configured cloud accounts. Configure credentials before running tasks that call cloud provider APIs.

For AWS, a common local check is:

```bash
aws sts get-caller-identity
```

Only run tasks against accounts and regions you intend to manage.

## Sensitive values

Sensitive outputs, such as generated administrator passwords or access tokens, should be filtered out of normal logs and stored in a secure location.

When creating new tasks or configuration examples:

- Avoid committing secrets.
- Prefer environment variables for sensitive values.
- Document required variables and safe defaults.
- Support dry-run behavior when a task can change infrastructure.

## Resource selection

Tasks should filter resources before taking action. A task should only affect resources that match the configured account, region, provider, labels, names, or other selection criteria.

This keeps cleanup and maintenance actions predictable, especially in multi-account and multi-region environments.

