# ⚡ GitHub Actions Events & Triggers Cheat Sheet

## What is an Event?

An **Event** is an activity that triggers a GitHub Actions workflow.

Examples include:

- Push
- Pull Request
- Manual Trigger
- Schedule
- Release
- Issue Creation

---

## Common Events

### Push

```yaml
on:
  push:
```

Runs whenever code is pushed to the repository.

---

### Pull Request

```yaml
on:
  pull_request:
```

Runs when a pull request is opened, synchronized, or reopened.

---

### Manual Trigger

```yaml
on:
  workflow_dispatch:
```

Allows users to manually start a workflow from the GitHub Actions tab.

---

### Scheduled Trigger

```yaml
on:
  schedule:
    - cron: "0 6 * * 1"
```

Runs automatically based on a cron schedule.

---

## Branch Filter

```yaml
on:
  push:
    branches:
      - main
```

Runs only when changes are pushed to the `main` branch.

---

## Multiple Events

```yaml
on:
  push:
  pull_request:
  workflow_dispatch:
```

A single workflow can listen to multiple events.

---

## Useful GitHub Context Variables

| Variable | Description |
|----------|-------------|
| github.actor | User who triggered the workflow |
| github.event_name | Event type |
| github.repository | Repository name |
| github.ref_name | Branch name |
| github.sha | Commit SHA |
| github.workflow | Workflow name |

---

## Best Practices

- Use branch filters when appropriate.
- Use manual triggers for deployments.
- Keep scheduled jobs lightweight.
- Use descriptive workflow names.

---

## Common Mistakes

- Forgetting branch filters.
- Incorrect cron expressions.
- Triggering deployments on every branch.
- Not testing manual workflows.

---

## Quick Revision

```
Event
   │
   ▼
Trigger
   │
   ▼
Workflow
   │
   ▼
Runner
   │
   ▼
Job
   │
   ▼
Step
```
