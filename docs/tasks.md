# Tasks

Tasks are the operational units Cloud Janitor runs. A task can create a cluster, clean up resources, run maintenance checks, or produce a report.

## Task workflow

A typical task follows this flow:

1. Read configuration.
2. Resolve defaults.
3. Validate credentials and required inputs.
4. Discover matching resources.
5. Apply safety checks.
6. Execute the operation.
7. Log results and write any reports.

## Safety expectations

Tasks that change cloud resources should be conservative by default.

- Validate all required configuration before making changes.
- Filter resources explicitly.
- Support dry-run mode when possible.
- Redact secrets from logs.
- Respect API limits and use retries with backoff.
- Record enough information for audit and troubleshooting.

## Example task categories

### Cluster creation

A cluster creation task can resolve provider defaults, validate configuration, create account-level resources, create cluster-level resources, wait for health checks, install plugins, and verify the resulting application.

### Account cleanup

An account cleanup task can find unused resources, confirm they match configured criteria, and remove them in a controlled order.

### Reporting

Reporting tasks can collect invocation results, summarize affected resources, and produce logs for later review.

## Adding new tasks

When adding a task, include:

- A clear task name
- Required configuration keys
- Safe defaults
- Expected side effects
- Dry-run behavior, if applicable
- Example usage

