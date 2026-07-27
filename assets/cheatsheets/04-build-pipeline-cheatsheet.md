# 🏗 GitHub Actions Build Pipeline Cheat Sheet

## What is a Build Pipeline?

A **Build Pipeline** automates the process of compiling, testing, packaging, and preparing an application for deployment.

---

## Typical Build Pipeline Flow

```
Checkout Repository
        │
        ▼
Setup Runtime
        │
        ▼
Install Dependencies
        │
        ▼
Run Tests
        │
        ▼
Build Application
        │
        ▼
Upload Artifact
        │
        ▼
Deploy
```

---

## Checkout Repository

```yaml
- uses: actions/checkout@v4
```

Downloads the repository onto the runner.

---

## Setup Node.js

```yaml
- uses: actions/setup-node@v4

  with:
    node-version: 20
```

Installs Node.js on the GitHub runner.

---

## Install Dependencies

```yaml
- run: npm install
```

Downloads all project dependencies.

---

## Run Tests

```yaml
- run: npm test
```

Executes automated tests.

---

## Build Project

```yaml
- run: npm run build
```

Generates the production build.

---

## Upload Build Artifact

```yaml
- uses: actions/upload-artifact@v4

  with:
    name: node-build
    path: dist/
```

Stores the build output for later jobs.

---

## Download Artifact

```yaml
- uses: actions/download-artifact@v4

  with:
    name: node-build
```

Retrieves the previously uploaded artifact.

---

## Artifact vs Cache

| Artifact | Cache |
|----------|-------|
| Shares build output | Speeds dependency installation |
| Used between jobs | Used between workflow runs |
| Stored temporarily | Reused automatically |

---

## Best Practices

- Run tests before deployment.
- Upload only required files.
- Use artifacts for deployment.
- Fail fast when tests fail.
- Keep build steps small and readable.

---

## Common Mistakes

- Skipping tests.
- Uploading unnecessary files.
- Hardcoding Node.js versions.
- Deploying without validating the build.

---

## Quick Revision

```
Checkout
     │
     ▼
Setup Node
     │
     ▼
Install
     │
     ▼
Test
     │
     ▼
Build
     │
     ▼
Artifact
     │
     ▼
Deploy
```
