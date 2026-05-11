# Getting started

Cloud Janitor can be run from source, as an executable JAR, as a container, or as a GitHub Action.

## Run from source

Use the Maven wrapper to start the Quarkus development mode:

```bash
./mvnw quarkus:dev
```

You can also start development mode with the Quarkus CLI:

```bash
quarkus dev
```

When using an IDE, run the `cj.Main` class.

## Run a task

After the application starts, run a task by passing the task name and any required configuration. The README notes that the default task is `marvin`, which logs a harmless reminder.

You can also explore available options with:

```bash
cloud-janitor -cj:help
```

## Use Gitpod

The repository includes Gitpod configuration with Java, Quarkus, AWS CLI, and supporting tools. After opening a Gitpod workspace, configure cloud credentials as needed. For AWS, verify credentials with:

```bash
aws sts get-caller-identity
```

## Package and run

Build a package with Maven, then run the generated artifact:

```bash
./mvnw package
java -jar target/*-runner.jar
```

## Run with Docker

Cloud Janitor can also be run from a container image:

```bash
docker run --pull=always cj/cloud-janitor
```

## Use as a GitHub Action

```yaml
- name: Cloud Janitor
  uses: CaravanaCloud/cloud-janitor@v1.7.3
```

