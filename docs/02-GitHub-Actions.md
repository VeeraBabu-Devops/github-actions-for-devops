# Chapter 02: GitHub Actions

> **Level:** Beginner to Intermediate
>
> **Prerequisites:** Basic Git & GitHub Knowledge
>
> **Estimated Reading Time:** 30–40 Minutes

---

# 📖 Introduction

Modern software development requires applications to be built, tested, and deployed quickly and reliably.

Traditionally, these tasks were performed manually, making software delivery slow, repetitive, and error-prone.

GitHub Actions solves this problem by providing built-in automation directly inside GitHub.

Instead of manually building or deploying applications every time code changes, developers can define workflows that automatically execute whenever specific events occur.

GitHub Actions is one of the most popular CI/CD platforms used by DevOps engineers because it integrates seamlessly with GitHub repositories.

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand GitHub Actions
- Understand CI/CD
- Learn GitHub Actions Architecture
- Understand Workflow Components
- Create Workflows
- Configure Events
- Understand Runners
- Create Jobs
- Create Steps
- Use Marketplace Actions
- Build your first GitHub Workflow

---

# 📑 Table of Contents

1. Introduction to GitHub Actions
2. Why GitHub Actions?
3. CI/CD Overview
4. Architecture
5. Components
6. Workflow
7. Events
8. Runner
9. Jobs
10. Steps
11. Actions

---

# 1. What is GitHub Actions?

## Definition

GitHub Actions is GitHub's built-in **Continuous Integration and Continuous Delivery (CI/CD)** automation platform.

It allows developers to automatically build, test, scan, package, and deploy applications whenever specific events occur in a GitHub repository. This aligns with the overview in your training notes. :contentReference[oaicite:1]{index=1}

Instead of performing repetitive tasks manually, GitHub Actions automates the entire software delivery process.

---

## Simple Definition

Think of GitHub Actions as a robot that watches your GitHub repository.

Whenever something happens, such as:

- Code is pushed
- Pull Request is opened
- Release is created
- Manual execution

GitHub Actions automatically performs the tasks you have defined.

---

## Example

Suppose a developer pushes new code.

Instead of manually running:

- Build
- Testing
- Docker Build
- Deployment

GitHub Actions performs everything automatically.

---

# Why Do We Need GitHub Actions?

Without automation:

Developer

↓

Write Code

↓

Build Manually

↓

Run Tests

↓

Deploy

↓

Repeat Every Time

This process is slow and error-prone.

---

With GitHub Actions:

Developer

↓

Push Code

↓

GitHub Actions

↓

Build

↓

Test

↓

Deploy

↓

Done

Everything is automated.

---

# Real-World Example

Imagine an online shopping application.

Whenever a developer pushes code:

- Application builds automatically.
- Unit tests execute.
- Security scans run.
- Docker image is created.
- Image is pushed to Docker Hub.
- Application is deployed to AWS.

No manual intervention is required.

---

# Key Features

GitHub Actions provides:

- CI/CD Automation
- Workflow Automation
- Event-Based Execution
- Cloud Runners
- Self-Hosted Runners
- Marketplace Actions
- Secrets Management
- Matrix Builds
- Multi-Platform Support

---

# Interview Tip

**Question**

What is GitHub Actions?

**Answer**

GitHub Actions is GitHub's built-in CI/CD automation platform used to automatically build, test, package, and deploy applications whenever predefined events occur inside a GitHub repository.

---

# 2. Why GitHub Actions?

GitHub Actions simplifies software automation by integrating directly with GitHub.

Developers do not need a separate CI/CD server for many common automation tasks.

---

## Advantages

- Built into GitHub
- Easy YAML syntax
- Supports Linux, Windows, and macOS runners
- Large Marketplace of reusable Actions
- Secure Secrets Management
- Easy integration with AWS, Azure, GCP, Docker, Kubernetes, Terraform, and more

---

## Typical DevOps Workflow

```
Developer

    │

Push Code

    │

GitHub Repository

    │

GitHub Actions

    │

Build

    │

Test

    │

Package

    │

Deploy

    │

Production
```

---

# Benefits

| Feature | Benefit |
|----------|----------|
| Automation | Eliminates manual work |
| Reliability | Reduces deployment errors |
| Speed | Faster software delivery |
| Integration | Works directly with GitHub |
| Flexibility | Supports many programming languages |

---

# Key Takeaways

- GitHub Actions is GitHub's native automation platform.
- It supports Continuous Integration and Continuous Delivery.
- Workflows are triggered by events.
- Automation improves software quality and delivery speed.

---

# ➡️ Next (Part 2)

In the next section, we'll cover:

- CI/CD Concepts
- GitHub Actions Architecture
- Workflow Components
- Workflow Lifecycle
- Architecture Diagram
---

# 3. Continuous Integration and Continuous Delivery (CI/CD)

Before learning GitHub Actions, it is important to understand the concepts of **Continuous Integration (CI)** and **Continuous Delivery/Deployment (CD)**.

GitHub Actions is primarily used to automate these software development practices.

---

## What is Continuous Integration (CI)?

Continuous Integration is the practice of automatically building and testing code whenever developers push changes to a shared repository.

Instead of waiting until the end of the development cycle, every code change is validated immediately.

### Continuous Integration Workflow

```text
Developer

    │

Write Code

    │

Commit

    │

Push

    │

GitHub Actions

    │

Build

    │

Run Tests

    │

Code Quality Checks

    │

Build Successful
```

---

### Benefits of Continuous Integration

- Detects bugs early
- Improves software quality
- Prevents integration issues
- Faster feedback
- Reduces manual testing

---

## What is Continuous Delivery (CD)?

Continuous Delivery automatically prepares applications for deployment after successful testing.

The deployment is ready, but a manual approval may still be required before releasing to production.

### Continuous Delivery Workflow

```text
Build

↓

Test

↓

Package

↓

Ready for Deployment

↓

Manual Approval

↓

Production
```

---

## What is Continuous Deployment?

Continuous Deployment goes one step further.

Once all tests pass successfully, the application is automatically deployed without manual approval.

```text
Build

↓

Test

↓

Package

↓

Deploy Automatically

↓

Production
```

---

## CI vs Continuous Delivery vs Continuous Deployment

| Feature | Continuous Integration | Continuous Delivery | Continuous Deployment |
|----------|------------------------|---------------------|------------------------|
| Build | ✅ | ✅ | ✅ |
| Test | ✅ | ✅ | ✅ |
| Package | ❌ | ✅ | ✅ |
| Manual Approval | ❌ | ✅ | ❌ |
| Automatic Production Deployment | ❌ | ❌ | ✅ |

---

## Real-World Example

Suppose your team develops an e-commerce application.

Whenever a developer pushes code:

1. GitHub Actions automatically builds the application.
2. Unit tests are executed.
3. Security scans are performed.
4. Docker image is created.
5. Docker image is pushed to Docker Hub.
6. Application is deployed to AWS.

This entire process is automated using GitHub Actions.

---

# 4. GitHub Actions Architecture

GitHub Actions follows an event-driven architecture.

Whenever an event occurs inside a GitHub repository, GitHub executes a predefined workflow.

---

## High-Level Architecture

```text
Developer
     │
     ▼
Git Push / Pull Request / Manual Trigger
     │
     ▼
GitHub Repository
     │
     ▼
Workflow (.github/workflows/*.yml)
     │
     ▼
Runner
     │
     ▼
Jobs
     │
     ▼
Steps
     │
     ▼
Actions / Shell Commands
     │
     ▼
Application Build / Test / Deploy
```

---

## Architecture Explanation

### Step 1 – Developer

A developer performs an action such as:

- Push Code
- Open Pull Request
- Create Release
- Click **Run Workflow**

These actions generate an event.

---

### Step 2 – GitHub Repository

GitHub receives the event and checks whether any workflow is configured for that event.

If a matching workflow exists, GitHub starts the workflow.

---

### Step 3 – Workflow

A workflow is a YAML file stored inside:

```text
.github/workflows/
```

Example:

```text
.github/workflows/main.yml
```

The workflow defines:

- Trigger
- Jobs
- Runner
- Steps
- Actions

---

### Step 4 – Runner

GitHub allocates a runner to execute the workflow.

A runner is simply a machine that performs the tasks defined in the workflow.

It can be:

- GitHub Hosted Runner
- Self-Hosted Runner

---

### Step 5 – Jobs

A workflow contains one or more jobs.

Each job performs a logical task.

Example:

```text
Workflow

├── Build Job

├── Test Job

└── Deploy Job
```

Jobs can execute:

- Sequentially
- In Parallel

---

### Step 6 – Steps

Each job contains multiple steps.

Example:

```text
Build Job

├── Checkout Code

├── Install Java

├── Maven Build

├── Run Tests

└── Upload Artifact
```

Steps execute one after another.

---

### Step 7 – Actions

Actions are reusable automation components.

Instead of writing lengthy shell scripts, you can reuse existing actions from the GitHub Marketplace.

Example:

```yaml
- uses: actions/checkout@v4
```

This downloads your repository to the runner.

---

## Complete Execution Flow

```text
Developer Pushes Code

        │

GitHub Detects Event

        │

Workflow Starts

        │

GitHub Creates Runner

        │

Runner Executes Job

        │

Job Executes Steps

        │

Steps Execute Actions

        │

Application Builds

        │

Tests Execute

        │

Deployment Starts
```

---

## Why This Architecture?

This design provides:

- Scalability
- Reliability
- Automation
- Fast Feedback
- Easy Maintenance

---

## Key Takeaways

- GitHub Actions automates CI/CD.
- CI validates code automatically.
- CD prepares or deploys applications.
- Workflows are triggered by repository events.
- Runners execute workflows.
- Workflows contain jobs.
- Jobs contain steps.
- Steps execute actions or shell commands.

---

# ➡️ Next (Part 3)

In the next section, we'll cover:

- GitHub Actions Components
- Workflow
- Workflow File Structure
- Workflow Syntax
- `name`
- `on`
- `env`
- `jobs`
- `runs-on`
- `steps`

---

# 5. GitHub Actions Components

GitHub Actions consists of several core components that work together to automate software development workflows.

Understanding these components is essential before writing workflow files.

---

## Core Components

| Component | Description |
|------------|-------------|
| Workflow | The complete automation pipeline |
| Event | Defines when the workflow should run |
| Runner | Machine that executes the workflow |
| Job | A group of related tasks |
| Step | An individual task within a job |
| Action | A reusable automation component |

---

## Component Relationship

```text
Workflow
│
├── Event
│
├── Runner
│
├── Job
│     │
│     ├── Step
│     ├── Step
│     └── Step
│
└── Action
```

---

# 6. Workflow

## What is a Workflow?

A **Workflow** is an automated pipeline that defines the tasks GitHub Actions should execute.

You can think of a Workflow as the equivalent of a Jenkins Pipeline.

| Jenkins | GitHub Actions |
|----------|----------------|
| Pipeline | Workflow |

A workflow is written in **YAML** format and stored in:

```text
.github/workflows/
```

Example:

```text
.github/workflows/main.yml
```

---

## Workflow Structure

Every workflow contains the following sections:

```yaml
name:
on:
env:
jobs:
```

---

## Complete Workflow Structure

```text
Workflow
│
├── name
├── on
├── env (Optional)
└── jobs
      │
      ├── Job 1
      │     ├── runs-on
      │     └── steps
      │            ├── Step 1
      │            ├── Step 2
      │            └── Step 3
      │
      └── Job 2
```

---

## Example Workflow

```yaml
name: CI Pipeline

on:
  push:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - run: echo "Hello GitHub Actions"
```

---

# Workflow Lifecycle

```text
Developer Pushes Code

↓

GitHub Detects Event

↓

Workflow Starts

↓

Runner Created

↓

Job Executes

↓

Steps Execute

↓

Workflow Completed
```

---

# 7. Workflow Keywords

Let's understand each workflow keyword in detail.

---

# name

## What is `name`?

The `name` keyword provides a human-readable name for the workflow.

This name appears in the **Actions** tab of the repository.

Example:

```yaml
name: CI Pipeline
```

---

## Benefits

- Easy identification
- Better readability
- Professional workflow names

---

## Best Practice

Use meaningful names.

Good:

```yaml
name: Build and Deploy
```

Avoid:

```yaml
name: Test
```

---

# on

## What is `on`?

The `on` keyword specifies **when the workflow should run**.

Without an event trigger, the workflow will never execute.

---

## Example

```yaml
on:
  push:
```

Whenever code is pushed to the repository, the workflow starts automatically.

---

## Multiple Events

```yaml
on:
  push:

  pull_request:

  workflow_dispatch:
```

Meaning:

- Push
- Pull Request
- Manual Execution

Any one of these events will trigger the workflow.

---

## Common Events

| Event | Description |
|--------|-------------|
| push | Trigger on code push |
| pull_request | Trigger on Pull Request |
| workflow_dispatch | Manual execution |
| schedule | Run on a schedule |
| release | Trigger when a release is published |

---

# env

## What is `env`?

The `env` section defines environment variables that can be used throughout the workflow.

Instead of repeating the same value multiple times, define it once.

---

## Example

```yaml
env:
  APP_NAME: ecommerce-app
  COMPANY: TechCorp
```

---

## Using Variables

```yaml
steps:
  - run: echo $APP_NAME
```

Output:

```text
ecommerce-app
```

---

## Benefits

- Cleaner workflows
- Easy maintenance
- Reusable values

---

# jobs

## What are Jobs?

A workflow contains one or more jobs.

Each job performs a logical task.

Examples:

- Build
- Test
- Package
- Deploy

---

## Example

```yaml
jobs:

  build:

  test:

  deploy:
```

---

## Job Execution

By default:

Jobs run **in parallel**.

If dependencies are required, use:

```yaml
needs:
```

Example:

```yaml
deploy:
  needs: build
```

This ensures the deploy job starts only after the build job completes successfully.

---

# runs-on

## What is `runs-on`?

The `runs-on` keyword specifies the operating system where the job executes.

---

## Example

```yaml
runs-on: ubuntu-latest
```

---

## Available Runners

```yaml
ubuntu-latest

windows-latest

macos-latest
```

---

## GitHub Hosted Runner

Workflow

↓

GitHub Creates Virtual Machine

↓

Runs Workflow

↓

Deletes Virtual Machine

A new runner is created for each workflow execution.

---

# steps

## What are Steps?

A **Step** is an individual task inside a job.

Examples include:

- Checkout Repository
- Install Java
- Build Project
- Run Tests
- Deploy Application

Steps execute sequentially.

---

## Example

```yaml
steps:

  - run: pwd

  - run: ls

  - run: whoami
```

---

## Multiple Commands

```yaml
steps:

  - name: System Information

    run: |

      echo "GitHub Actions Demo"

      date

      hostname

      free -m

      df -h
```

---

## Workflow Execution Example

```text
Workflow

↓

Build Job

↓

Step 1
Checkout Code

↓

Step 2
Install Java

↓

Step 3
Build

↓

Step 4
Test

↓

Step 5
Package
```

---

# Best Practices

- Give meaningful names to workflows.
- Use descriptive job names.
- Keep jobs independent where possible.
- Store reusable values in `env`.
- Break large workflows into multiple jobs.
- Keep steps focused on a single task.

---

# Key Takeaways

- A Workflow is the complete automation pipeline.
- Events trigger workflows.
- Runners execute jobs.
- Jobs contain steps.
- Steps perform individual tasks.
- Environment variables improve workflow maintainability.

---

# ➡️ Next (Part 4)

We'll cover:

- Actions (`uses`)
- GitHub Marketplace
- GitHub Hosted vs Self-Hosted Runners
- First Workflow
- Running Multiple Jobs
- Workflow Dependencies
- Manual Triggers
