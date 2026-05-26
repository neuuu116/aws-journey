# S3 (Simple Storage Service) — Concepts

---

## What is S3?
Object storage service by AWS. Store any type of file (images, videos, backups, code, datasets) as objects inside **buckets**.

---

## Core Concepts

### Bucket Versioning
- Keeps multiple versions of the same object in the same bucket
- If you overwrite or delete a file, old versions are preserved
- Useful for: backups, rollback, accidental delete protection

### Bucket ABAC (Attribute-Based Access Control)
- Strategy to define permissions based on **attributes** (tags)
- Instead of writing policies per user, you attach tags and control access via those tags
- Example: `department=engineering` tag → only engineering team can access

### Tags
- Key-value pairs attached to buckets or objects
- Used to:
  - Track storage cost (billing per tag)
  - Specify permissions (ABAC)
  - Organize resources

### Encryption

| Type | What it means |
|---|---|
| **SSE-S3** | Server-side encryption using AWS-managed keys (default, simplest) |
| **SSE-KMS** | Uses AWS Key Management Service — more control, audit trail |

- **Bucket key (KMS)** — encrypts new objects uploaded to the bucket using a KMS key

### Metadata
- You can create metadata (configuration data) for a bucket
- Stores info about the bucket/object — content-type, custom tags, etc.

### S3 URI
- Format: `s3://bucket-name/object-key`
- Example: `s3://my-resume-bucket/resumes/neha_resume.pdf`
- Used in AWS CLI, SDKs, and services like Glue, Athena

### Access Points
- Can create access points for general purpose buckets
- Must specify **network origin**:
  - **VPC (Virtual Private Cloud)** — private access only within AWS network
  - **Internet** — public access
- Can also **block public access** completely at bucket level

---

## Key Rules to Remember

- Bucket names are **globally unique** across all AWS accounts
- S3 is **region-specific** but bucket names are global
- Default: all buckets are **private**
- Free tier: 5 GB standard storage, 20,000 GET requests, 2,000 PUT requests/month

---

## What's Next (To Do)
- [ ] Create a bucket via AWS Console
- [ ] Upload a file and access via S3 URI
- [ ] Enable versioning and test overwrite
- [ ] Set bucket policy to block public access
- [ ] Try SSE-S3 encryption on upload
