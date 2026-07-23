# Chapter 04: GitHub Actions Workflow Events

> **Level:** Beginner to Intermediate
>
> **Prerequisites:** GitHub Actions Fundamentals
>
> **Estimated Reading Time:** 35 Minutes

---

# 📖 Introduction

A workflow without an event will never execute.

Events tell GitHub **when** a workflow should start.

Whenever an event occurs, GitHub checks the repository for matching workflow files and executes them automatically.

Think of an event as a trigger that starts the automation process.

---

# 🎯 Learning Objectives

After completing this chapter, you will understand:

- What are Workflow Events
- Push Event
- Pull Request Event
- Manual Event
- Schedule Event
- Release Event
- Branch Filters
- Path Filters
- Multiple Triggers
- Production Trigger Strategies

---

# Workflow Event Architecture

```mermaid
flowchart LR
    Developer --> Push
    Developer --> Pull_Request
    Developer --> Manual
    Developer --> Release
    Developer --> Schedule

    Push --> Workflow
    Pull_Request --> Workflow
    Manual --> Workflow
    Release --> Workflow
    Schedule --> Workflow

    Workflow --> Runner
```

---

# What is an Event?

An Event is an activity that occurs inside a GitHub repository.

Examples include:

- Pushing code
- Opening a Pull Request
- Creating a Release
- Clicking "Run Workflow"
- Scheduled execution

Whenever these activities occur, GitHub can automatically start a workflow.

---

# Event Flow

```mermaid
flowchart TD
    Developer --> GitHub_Repository
    GitHub_Repository --> Event
    Event --> Workflow
    Workflow --> Runner
    Runner --> Jobs
```
---

# Common Events

| Event | Description |
|--------|-------------|
| push | Trigger when code is pushed |
| pull_request | Trigger on Pull Requests |
| workflow_dispatch | Manual execution |
| schedule | Scheduled execution |
| release | Release published |

---

# Why Events Matter

Imagine an application with:

- 50 Developers
- Hundreds of Commits
- Multiple Releases every week

Running workflows manually every time would be impossible.

Events automate this process.

---

# Real-world Example

Developer pushes code.

↓

GitHub detects Push Event.

↓

Workflow starts.

↓

Runner created.

↓

Application builds automatically.

↓

Tests execute.

↓

Deployment begins.

---

## 🔄 Event Lifecycle

```mermaid
flowchart TD

A([Developer Action])

B([GitHub Repository])

C([Event Triggered])

D([Workflow Started])

E([GitHub Runner Created])

F([Jobs Executed])

G([Workflow Completed])

A --> B
B --> C
C --> D
D --> E
E --> F
F --> G
```

---

# Benefits

- Complete Automation

- No Manual Work

- Faster Delivery

- Immediate Feedback

- Consistent Deployments

---

# Interview Tip

### Question

What is an Event?

### Expected Answer

An Event is an activity that occurs inside a GitHub repository and triggers a GitHub Actions workflow.

Examples include Push, Pull Request, Manual Execution, Release, and Schedule.

---

# Common Mistakes

❌ Forgetting to define an event

❌ Wrong event syntax

❌ Using incorrect branch filters

❌ Triggering unnecessary workflows

---

# Best Practices

✅ Trigger workflows only when necessary

✅ Filter by branch

✅ Filter by path

✅ Use manual triggers for production deployments

---

# Hands-on Exercise

Create a workflow that:

- Executes only on Push
- Prints

  - Date

  - Hostname

  - Current User

Push code and observe the Actions tab.

---

# Key Takeaways

- Events trigger workflows.
- Without an event, a workflow never starts.
- GitHub supports many event types.
- Events can be filtered for better control.

---

# ➡️ Next (Part 2)

We'll cover:

- Push Event
- Push on Specific Branch
- Branch Filters
- Multiple Branches
- Tag Events

---

# 🚀 Push Event

The **Push Event** is the most commonly used trigger in GitHub Actions.

Whenever a developer pushes code to a repository, GitHub automatically starts the workflow.

---

## Push Event Architecture

```mermaid
flowchart LR

A([Developer])

B([Git Push])

C([GitHub Repository])

D([Push Event])

E([Workflow])

F([Runner])

A --> B
B --> C
C --> D
D --> E
E --> F
```

---

## Basic Push Trigger

```yaml
on:
  push:
```

This workflow executes whenever code is pushed to any branch.

---

## Real-world Example

Developer pushes new code.

↓

GitHub detects Push Event.

↓

Workflow starts automatically.

↓

Application builds.

↓

Tests execute.

↓

Deployment begins.

---

# Push on Specific Branch

In production environments, workflows should not execute for every branch.

Instead, trigger workflows only on important branches.

Example:

```yaml
on:

  push:

    branches:

      - main
```

Only pushes to the **main** branch trigger the workflow.

---

# Multiple Branches

You can monitor multiple branches.

```yaml
on:

  push:

    branches:

      - main

      - develop

      - release/**
```

---

## Branch Flow

```mermaid
flowchart TD

A([Developer Push])

B{Branch?}

C([main])

D([develop])

E([release/*])

F([Workflow])

A --> B
B --> C
B --> D
B --> E

C --> F
D --> F
E --> F
```

---

## Real-world Example

Repository contains:

```
main

develop

feature/login

feature/payment

release/v1
```

Workflow executes only on:

- main
- develop
- release/*

Feature branches are ignored.

---

# Ignoring Branches

Sometimes certain branches should never trigger workflows.

Example:

```yaml
on:

  push:

    branches-ignore:

      - experimental

      - test/*
```

---

# Tag Events

GitHub can trigger workflows whenever tags are pushed.

Example:

```yaml
on:

  push:

    tags:

      - v*
```

---

## Tag Workflow

```
Developer

↓

Create Tag

↓

Push Tag

↓

Workflow Executes
```

---

# Path Filters

Sometimes only specific files should trigger workflows.

Example:

```yaml
on:

  push:

    paths:

      - src/**

      - pom.xml
```

Workflow executes only when:

- Source code changes
- pom.xml changes

---

## Ignore Paths

Example:

```yaml
on:

  push:

    paths-ignore:

      - README.md

      - docs/**
```

Documentation changes will not trigger the workflow.

---

## Path Filter Architecture

```mermaid
flowchart LR

A([Developer Push])

B([Files Changed])

C{Matches Path Filter?}

D([Run Workflow])

E([Ignore])

A --> B
B --> C
C -->|Yes| D
C -->|No| E
```

---

# Branch vs Path Filter

| Branch Filter | Path Filter |
|--------------|-------------|
| Filters branches | Filters files |
| Example: main | Example: src/** |
| Used for environments | Used for selective builds |

---

# Production Strategy

Large organizations commonly use:

| Branch | Workflow |
|---------|----------|
| feature/* | Build Only |
| develop | Build + Unit Test |
| release/* | Full QA Pipeline |
| main | Production Deployment |

---

# Best Practices

✅ Trigger workflows only on required branches

✅ Ignore documentation updates

✅ Use path filters to reduce unnecessary workflow runs

✅ Separate development and production workflows

---

# Common Mistakes

❌ Triggering workflows on every branch

❌ No branch filters

❌ No path filters

❌ Running expensive deployments unnecessarily

---

# Interview Tip

### Question

How do you trigger a workflow only for the `main` branch?

### Expected Answer

```yaml
on:

  push:

    branches:

      - main
```

---

# Hands-on Exercise

Create a workflow that:

- Executes only on the `main` branch.
- Prints:
  - Current date
  - Hostname
  - Current user

Push code to:

- `main`
- `develop`

Observe which branch triggers the workflow.

---

# Key Takeaways

- `push` is the most commonly used event.
- Branch filters control which branches trigger workflows.
- Path filters control which files trigger workflows.
- Tag events support release automation.

---

# ➡️ Next (Part 3)

We'll cover:

- Pull Request Event
- Manual Trigger
- Schedule Event
- Release Event
- Multiple Events
- Production Trigger Strategies

---

# 🔀 Pull Request Event

A **Pull Request Event** triggers a workflow whenever a Pull Request is created, updated, or reopened.

Unlike the `push` event, this trigger focuses on code review and validation before merging changes into the target branch.

---

## Why Use Pull Request Events?

In professional DevOps teams, code is **not merged directly** into the `main` branch.

Instead:

1. Developer creates a feature branch.
2. Developer pushes code.
3. A Pull Request is opened.
4. GitHub Actions automatically:
   - Builds the application
   - Runs unit tests
   - Executes security checks
   - Reports the results

Only after all checks pass is the Pull Request approved and merged.

---

## Pull Request Workflow

```mermaid
flowchart TD

A([Developer])

B([Feature Branch])

C([Push Code])

D([Open Pull Request])

E([GitHub Actions])

F([Build])

G([Tests])

H([Code Review])

I([Merge])

A --> B
B --> C
C --> D
D --> E
E --> F
F --> G
G --> H
H --> I
```

---

## Basic Pull Request Trigger

```yaml
on:

  pull_request:
```

Runs whenever a Pull Request is opened, synchronized, or reopened.

---

## Pull Request on Main Branch

```yaml
on:

  pull_request:

    branches:

      - main
```

Only Pull Requests targeting **main** trigger the workflow.

---

## Pull Request Types

GitHub allows workflows to execute only for specific Pull Request actions.

Example:

```yaml
on:

  pull_request:

    types:

      - opened

      - synchronize

      - reopened
```

---

## Most Common Pull Request Types

| Type | Description |
|------|-------------|
| opened | PR created |
| synchronize | New commits pushed to PR |
| reopened | Previously closed PR reopened |
| closed | PR closed |
| ready_for_review | Draft PR marked ready |

---

# ✋ Manual Trigger (`workflow_dispatch`)

Some workflows should not execute automatically.

Examples:

- Production Deployment
- Database Migration
- Disaster Recovery
- Infrastructure Changes

GitHub provides a manual trigger called:

```yaml
workflow_dispatch
```

---

## Example

```yaml
on:

  workflow_dispatch:
```

---

## Manual Workflow Diagram

```mermaid
flowchart TD

A([User])

B([Actions Tab])

C([Run Workflow])

D([GitHub Workflow])

E([Runner])

F([Workflow Completed])

A --> B
B --> C
C --> D
D --> E
E --> F
```

---

## Benefits

- Manual execution
- Safe production deployments
- Easy testing
- Controlled releases

---

# ⏰ Scheduled Event

GitHub can execute workflows automatically using **Cron expressions**.

Example:

Every day at midnight:

```yaml
on:

  schedule:

    - cron: '0 0 * * *'
```

---

## Cron Format

```
┌──────── Minute
│ ┌────── Hour
│ │ ┌──── Day of Month
│ │ │ ┌── Month
│ │ │ │ ┌─ Day of Week
│ │ │ │ │
* * * * *
```

---

## Common Cron Examples

| Schedule | Cron |
|-----------|------|
| Every hour | `0 * * * *` |
| Every day at midnight | `0 0 * * *` |
| Every Monday | `0 0 * * 1` |
| Every Sunday | `0 0 * * 0` |

---

## Schedule Workflow

```mermaid
flowchart LR

A([GitHub Scheduler])

B([Cron Time])

C([Workflow])

D([Runner])

A --> B
B --> C
C --> D
```

---

# 🚀 Release Event

Release events are useful when publishing software versions.

Example:

```yaml
on:

  release:

    types:

      - published
```

Whenever a new GitHub Release is published:

- Build application
- Upload release files
- Publish Docker image
- Notify users

---

## Release Pipeline

```mermaid
flowchart TD

A([Release Published])

B([Workflow])

C([Build])

D([Package])

E([Publish])

A --> B
B --> C
C --> D
D --> E
```

---

# 🔥 Multiple Events

A workflow can respond to multiple events.

Example:

```yaml
on:

  push:

  pull_request:

  workflow_dispatch:
```

This single workflow can execute for:

- Push
- Pull Request
- Manual execution

---

## Multiple Trigger Flow

```mermaid
flowchart LR

A([Push])

B([Pull Request])

C([Manual])

D([Workflow])

A --> D
B --> D
C --> D
```

---

# 🏢 Production Trigger Strategy

A common enterprise strategy:

| Event | Purpose |
|--------|----------|
| push | Continuous Integration |
| pull_request | Code Validation |
| workflow_dispatch | Production Deployment |
| schedule | Maintenance |
| release | Software Release |

---

# 💡 Best Practices

- Use `push` for CI pipelines.
- Use `pull_request` for code validation.
- Use `workflow_dispatch` for production deployments.
- Use `schedule` for maintenance jobs.
- Use `release` for software publishing.

---

# ⚠️ Common Mistakes

❌ Deploying to production on every push

❌ No Pull Request validation

❌ Running scheduled jobs too frequently

❌ Forgetting branch filters

---

# 🎯 Interview Tip

### Question

What is the difference between `push` and `pull_request`?

### Expected Answer

- `push` triggers when code is pushed to a repository.
- `pull_request` triggers when a Pull Request is created, updated, or reopened.

---

# 📝 Hands-on Exercise

Create one workflow that supports:

- Push
- Pull Request
- Manual Trigger

Verify that each event successfully starts the workflow.

---

# 🔑 Key Takeaways

- `pull_request` validates code before merging.
- `workflow_dispatch` enables manual execution.
- `schedule` automates recurring tasks.
- `release` supports software publishing.
- One workflow can respond to multiple events.

---

# ➡️ Next (Final Part)

We'll complete Chapter 4 with:

- Production Event Strategy
- Event Best Practices
- Event Troubleshooting
- Chapter Summary
- 30 Interview Questions
