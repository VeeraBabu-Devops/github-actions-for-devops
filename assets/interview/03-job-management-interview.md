# 🎯 GitHub Actions Interview Questions - Job Management

## 1. What is a Job?

A Job is a collection of related steps executed on the same runner.

---

## 2. What is the difference between a Job and a Step?

| Job | Step |
|------|------|
| Contains multiple steps | Executes one task |
| Runs on a runner | Runs inside a job |

---

## 3. What is `needs`?

The `needs` keyword creates job dependencies.

Example:

```yaml
deploy:
  needs: test
```

---

## 4. Can multiple jobs run simultaneously?

Yes.

Jobs without `needs` execute in parallel.

---

## 5. What happens if a job fails?

Dependent jobs are skipped unless explicitly configured otherwise.

---

## 6. What are Repository Variables?

Repository Variables store non-sensitive configuration values.

Example:

```yaml
${{ vars.APP_NAME }}
```

---

## 7. What are GitHub Secrets?

Secrets securely store sensitive information such as:

- AWS Keys
- Passwords
- Tokens
- API Keys

---

## 8. Difference between Variables and Secrets?

| Variables | Secrets |
|------------|----------|
| Visible | Encrypted |
| Configuration | Credentials |

---

## 9. What is an Environment Variable?

An Environment Variable is defined using `env:` and is available during workflow execution.

---

## 10. Why use multiple jobs?

- Faster execution
- Better organization
- Parallel processing
- Easier troubleshooting

---

## 11. Explain your Job Management workflow.

A good answer:

"I created three independent jobs (Build, Security Scan, and Code Quality Check) that run in parallel. The Test job waits for all three using `needs`, and the Deploy job runs only after the Test job succeeds. This demonstrates both parallel and sequential execution."
