# 📝 AWS S3 Deployment Quiz

## Question 1

Which AWS service hosts a static website?

- A. EC2
- B. Lambda
- C. Amazon S3
- D. RDS

**Answer:** C

---

## Question 2

Where should AWS credentials be stored?

- A. README
- B. Workflow YAML
- C. GitHub Secrets
- D. package.json

**Answer:** C

---

## Question 3

Which command uploads files to S3?

- A. aws s3 upload
- B. aws s3 sync
- C. aws copy
- D. aws deploy

**Answer:** B

---

## Question 4

Why is CloudFront used?

- A. Database
- B. DNS
- C. CDN and caching
- D. Compute

**Answer:** C

---

## Question 5

What removes cached content from CloudFront?

- A. Refresh
- B. Restart
- C. Cache Invalidation
- D. Sync

**Answer:** C

---

## True or False

GitHub Secrets should be used to store AWS Access Keys.

**Answer:** True

---

## Scenario

Your website is updated in S3, but users still see the old version.

What should you do?

**Answer:**

Create a CloudFront cache invalidation to refresh the cached content.
