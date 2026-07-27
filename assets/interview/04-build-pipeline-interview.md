# 🎯 GitHub Actions Interview Questions - Build Pipeline

## 1. What is a Build Pipeline?

A Build Pipeline automates the process of building, testing, packaging, and preparing an application for deployment.

---

## 2. Why do we use `actions/checkout`?

It downloads the repository source code onto the GitHub runner.

---

## 3. Why is `actions/setup-node` required?

It installs the required Node.js version before running Node.js commands.

---

## 4. Why run `npm install`?

It installs all project dependencies listed in `package.json`.

---

## 5. What does `npm run build` do?

It creates a production-ready build of the application.

---

## 6. What is an Artifact?

An artifact is a file or directory generated during a workflow and shared with other jobs.

---

## 7. Difference between Artifact and Cache?

| Artifact | Cache |
|----------|-------|
| Stores build output | Stores dependencies |
| Shared between jobs | Speeds future builds |

---

## 8. Why upload artifacts?

To make build outputs available to deployment jobs.

---

## 9. What happens if the build fails?

The workflow stops, and dependent jobs are skipped.

---

## 10. Explain your Build Pipeline.

Example answer:

"I created a GitHub Actions workflow that checks out the repository, sets up Node.js, installs dependencies, builds the application, uploads the build artifact, and then downloads it in a deployment simulation job."
