# 🎯 GitHub Actions Interview Questions - Events & Triggers

## 1. What is an Event?

An event is an activity that starts a GitHub Actions workflow.

Examples:

- push
- pull_request
- workflow_dispatch
- schedule

---

## 2. What is the difference between push and pull_request?

| Push | Pull Request |
|------|--------------|
| Triggered after code is pushed | Triggered when a PR is opened or updated |

---

## 3. What is workflow_dispatch?

It allows a workflow to be started manually from the GitHub Actions page.

---

## 4. What is a scheduled workflow?

A workflow triggered automatically using a cron expression.

Example:

```yaml
schedule:
  - cron: "0 6 * * 1"
```

---

## 5. Can a workflow have multiple triggers?

Yes.

Example:

```yaml
on:
  push:
  pull_request:
  workflow_dispatch:
```

---

## 6. What is github.actor?

The username of the person or system that triggered the workflow.

---

## 7. What is github.sha?

The commit ID that triggered the workflow.

---

## 8. What is github.ref_name?

The branch or tag name that triggered the workflow.

---

## 9. Why use branch filters?

To prevent workflows from running on every branch unnecessarily.

---

## 10. What happens after an event occurs?

1. Event occurs
2. GitHub checks workflow triggers
3. Runner starts
4. Jobs execute
5. Workflow completes
