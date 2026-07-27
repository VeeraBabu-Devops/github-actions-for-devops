# 📝 GitHub Actions Job Management Quiz

## Question 1

Which keyword creates job dependencies?

- A. depends
- B. after
- C. needs
- D. require

**Answer:** C

---

## Question 2

Jobs without `needs` run:

- A. Sequentially
- B. Parallel
- C. Manually
- D. Randomly

**Answer:** B

---

## Question 3

Where should passwords be stored?

- A. Repository Variables
- B. YAML file
- C. GitHub Secrets
- D. README

**Answer:** C

---

## Question 4

Which keyword defines environment variables?

- A. env
- B. vars
- C. config
- D. environment

**Answer:** A

---

## Question 5

Which value is encrypted?

- A. Repository Variable
- B. GitHub Secret
- C. Workflow Name
- D. Job Name

**Answer:** B

---

## True or False

A job can contain multiple steps.

**Answer:** True

---

## Scenario

You have four jobs:

- Build
- Security Scan
- Test
- Deploy

Deploy should run only after Test succeeds.

Which keyword will you use?

**Answer:**

```yaml
needs: test
```

---

## Scenario

Build, Security Scan, and Lint should start together.

Should you use `needs`?

**Answer:** No. Leave them without dependencies so they run in parallel.
