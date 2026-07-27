# 🔄 GitHub Actions Job Management Cheat Sheet

## What is a Job?

A **Job** is a collection of related steps that run on the same runner.

---

## Job Structure

```yaml
jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - run: echo "Building..."
```

---

## Multiple Jobs

```yaml
jobs:
  build:
    ...

  test:
    ...

  deploy:
    ...
```

Each job gets its own runner unless dependencies are specified.

---

## Job Dependency (`needs`)

```yaml
deploy:
  needs: build
```

The `deploy` job starts only after the `build` job completes successfully.

---

## Multiple Dependencies

```yaml
test:
  needs:
    - build
    - security
    - lint
```

The `test` job waits for all listed jobs to finish successfully.

---

## Parallel Execution

Jobs without `needs` run simultaneously.

Example:

```
Build

Security Scan

Code Quality Check
```

---

## Sequential Execution

```
Build
   │
   ▼
Test
   │
   ▼
Deploy
```

---

## Workflow Architecture

```
             Build
            /     \
           ▼       ▼
     Security   Lint
           \     /
            ▼   ▼
             Test
              │
              ▼
           Deploy
```

---

## Environment Variables

```yaml
env:
  APP_NAME: github-actions-demo
```

Access:

```yaml
echo "$APP_NAME"
```

---

## Repository Variables

```yaml
${{ vars.APP_NAME }}
```

Used for non-sensitive configuration.

---

## GitHub Secrets

```yaml
${{ secrets.AWS_ACCESS_KEY_ID }}
```

Used for passwords, API keys, tokens, and credentials.

---

## Best Practices

- Keep jobs focused on a single responsibility.
- Use `needs` to define dependencies.
- Store credentials in GitHub Secrets.
- Use Repository Variables for configuration values.
- Keep jobs independent whenever possible.

---

## Common Mistakes

- Hardcoding passwords.
- Creating unnecessary job dependencies.
- Running everything in one job.
- Using variables instead of secrets for credentials.

---

## Quick Revision

```
Workflow
    │
    ▼
Jobs
    │
    ▼
Steps
```

```
Jobs without needs

↓

Parallel Execution
```

```
needs

↓

Sequential Execution
```
