# 📝 GitHub Actions Events & Triggers Quiz

## Question 1

Which event runs when code is pushed?

- A. workflow_dispatch
- B. push
- C. release
- D. issue

**Answer:** B

---

## Question 2

Which event allows manual execution?

- A. schedule
- B. workflow_dispatch
- C. push
- D. merge

**Answer:** B

---

## Question 3

Which event runs for Pull Requests?

- A. pull_request
- B. push
- C. release
- D. issue

**Answer:** A

---

## Question 4

Which keyword limits execution to a branch?

- A. runner
- B. branches
- C. step
- D. jobs

**Answer:** B

---

## Question 5

Which GitHub context variable stores the user who triggered the workflow?

- A. github.repository
- B. github.sha
- C. github.actor
- D. github.job

**Answer:** C

---

## True or False

A workflow can have multiple events.

**Answer:** True

---

## Scenario

You want a deployment workflow to run only when code is merged into the `main` branch.

Which event and filter would you use?

**Answer:**

```yaml
on:
  push:
    branches:
      - main
```
