# ☁️ GitHub Actions AWS S3 Deployment Cheat Sheet

## What is CI/CD Deployment?

Continuous Deployment (CD) automates the release of applications to cloud platforms after a successful build and test.

---

## Deployment Architecture

```
Developer
     │
     ▼
GitHub Repository
     │
     ▼
GitHub Actions
     │
     ▼
GitHub Hosted Runner
     │
     ▼
AWS IAM User
     │
     ▼
Amazon S3 Bucket
     │
     ▼
CloudFront Distribution
     │
     ▼
End Users
```

---

## Required AWS Services

- IAM User
- S3 Bucket
- CloudFront Distribution
- GitHub Secrets

---

## GitHub Secrets

Store the following credentials securely:

```text
AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

AWS_REGION

S3_BUCKET_NAME

CLOUDFRONT_DISTRIBUTION_ID
```

Never store AWS credentials directly in your workflow.

---

## Configure AWS Credentials

```yaml
- uses: aws-actions/configure-aws-credentials@v4

  with:
    aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
    aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    aws-region: ${{ secrets.AWS_REGION }}
```

---

## Upload Files to S3

```bash
aws s3 sync ./dist s3://my-bucket --delete
```

---

## CloudFront Cache Invalidation

```bash
aws cloudfront create-invalidation \
  --distribution-id ABC123XYZ \
  --paths "/*"
```

---

## Deployment Flow

```
Push Code
     │
     ▼
Build Project
     │
     ▼
Upload Artifact
     │
     ▼
Configure AWS
     │
     ▼
Upload to S3
     │
     ▼
Invalidate CloudFront
     │
     ▼
Website Updated
```

---

## Best Practices

- Use GitHub Secrets for credentials.
- Grant minimum IAM permissions.
- Enable bucket versioning.
- Use CloudFront for caching.
- Test deployments before production.

---

## Common Mistakes

- Committing AWS keys to GitHub.
- Making the S3 bucket public without proper controls.
- Forgetting CloudFront invalidation.
- Giving IAM users excessive permissions.

---

## Quick Revision

```
GitHub

↓

Workflow

↓

AWS Credentials

↓

S3 Upload

↓

CloudFront

↓

Live Website
```
