# 📄 GitHub Actions Workflow Cheat Sheet

## What is a Workflow?

A **Workflow** is an automated process defined in a YAML file that runs one or more jobs based on specific events.

---

## Workflow Location

```text
.github/workflows/
```

---

## Basic Workflow Structure

```yaml
name: Basic Workflow

on:
  workflow_dispatch:

jobs:
  demo:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Display Message
        run: echo "Hello GitHub Actions"
```

---

## Main Components

| Component | Description |
|-----------|-------------|
| Workflow | Complete automation process |
| Event | Trigger that starts the workflow |
| Job | Collection of related steps |
| Step | Individual task within a job |
| Runner | Machine that executes the workflow |
| Action | Reusable automation component |

---

## Common Triggers

```yaml
on:
  push:
```

```yaml
on:
  pull_request:
```

```yaml
on:
  workflow_dispatch:
```

```yaml
on:
  schedule:
```

---

## Runner Examples

```yaml
runs-on: ubuntu-latest
```

```yaml
runs-on: windows-latest
```

```yaml
runs-on: macos-latest
```

---

## Useful Commands

```yaml
pwd
```

```yaml
ls -la
```

```yaml
echo "Hello"
```

```yaml
date
```

```yaml
whoami
```

---

## Best Practices

- Use meaningful workflow names.
- Keep workflows focused on one purpose.
- Use `actions/checkout` before accessing repository files.
- Give every step a descriptive name.
- Store sensitive information in GitHub Secrets.

---

## Common Mistakes

- Incorrect YAML indentation.
- Missing checkout step.
- Hardcoding passwords or tokens.
- Using unclear step names.

---

## Interview Tip

Remember this hierarchy:

```
Workflow
    │
    ▼
Job
    │
    ▼
Step
```
