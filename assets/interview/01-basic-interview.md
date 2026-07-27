# 🎯 GitHub Actions Interview Questions (Basic)

## 1. What is GitHub Actions?

**Answer:**

GitHub Actions is GitHub's built-in CI/CD platform that automates software development workflows such as building, testing, and deploying applications.

---

## 2. What is a Workflow?

A workflow is an automated process defined in a YAML file that contains one or more jobs.

---

## 3. Where are workflow files stored?

```
.github/workflows/
```

---

## 4. What is a Runner?

A runner is the machine that executes workflow jobs.

Examples:

- Ubuntu
- Windows
- macOS
- Self-hosted Runner

---

## 5. What is a Job?

A job is a group of related steps executed on the same runner.

---

## 6. What is a Step?

A step is a single task inside a job.

Example:

```yaml
- name: Print Message
  run: echo "Hello"
```

---

## 7. What is an Action?

An action is a reusable component that performs a predefined task.

Example:

```yaml
uses: actions/checkout@v4
```

---

## 8. Difference between Job and Step?

| Job | Step |
|------|------|
| Contains multiple steps | Performs one task |
| Runs on a runner | Runs inside a job |

---

## 9. What happens when a workflow starts?

1. Event occurs
2. GitHub creates a runner
3. Jobs execute
4. Runner is destroyed

---

## 10. What is CI/CD?

CI – Continuous Integration

CD – Continuous Delivery / Continuous Deployment
