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
