# 🎯 GitHub Actions Interview Questions - AWS Deployment

## 1. Why use GitHub Actions for deployment?

GitHub Actions automates application deployment after successful builds and tests.

---

## 2. Why are GitHub Secrets required?

They securely store sensitive credentials such as AWS Access Keys.

---

## 3. Which AWS services are used in your deployment?

- IAM
- Amazon S3
- CloudFront

---

## 4. Why use Amazon S3?

Amazon S3 hosts static website files such as HTML, CSS, JavaScript, and images.

---

## 5. Why use CloudFront?

CloudFront improves performance using edge caching and HTTPS.

---

## 6. What is CloudFront Cache Invalidation?

It removes cached files so users receive the latest version of the application.

---

## 7. Which command uploads files to S3?

```bash
aws s3 sync
```

---

## 8. What permissions should the IAM user have?

Only the permissions required for deployment (principle of least privilege).

---

## 9. What happens if deployment fails?

The workflow stops, and the website remains unchanged until the issue is fixed.

---

## 10. Explain your deployment workflow.

Example answer:

"My GitHub Actions workflow builds the Node.js application, uploads the build artifact, configures AWS credentials using GitHub Secrets, synchronizes the build output to an Amazon S3 bucket, and invalidates the CloudFront cache so users receive the latest version."
