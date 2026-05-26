# AWS Journey 🚀

Self-learning AWS from scratch — hands-on first, theory second.  
No paid courses. Just the console, CLI, and real projects.

---

## Progress Tracker

| Service | Concepts | Hands-On | Notes |
|---|---|---|---|
| S3 | ✅ | 🔄 In Progress | [s3/notes.md](./s3/notes.md) |
| IAM | 🔄 In Progress | 🔄 In Progress | — |
| EC2 | ✅ | ✅ | [ec2/hands-on.md](./ec2/hands-on.md) |

---

## Structure

```
aws-journey/
├── ec2/
│   └── hands-on.md       # Launched EC2 instance, AMI selection, key pairs, storage
├── s3/
│   └── notes.md          # Versioning, ABAC, encryption, access points, S3 URI
├── iam/
│   └── notes.md          # (coming soon)
└── README.md
```

---

## What I've Done So Far

### EC2
- Launched a `t3.micro` instance (Amazon Linux 2023) in `eu-north-1`
- Configured storage: gp3 SSD
- Created RSA key pair (.pem) for SSH access
- Understood AMI architecture mismatch (macOS vs standard instance types)
- Instance running with public IP assigned

### S3
- Studied core concepts: versioning, ABAC, tags, encryption (SSE-S3, SSE-KMS)
- S3 URI format, access points, VPC vs internet network origin
- Public access blocking

### IAM
- In progress

---

## Goal

Deploy a real backend project (FastAPI) on EC2 with:
- S3 for file storage
- IAM roles for secure access (no hardcoded keys)
- RDS or DynamoDB for database

---

## Stack Being Learned
`EC2` · `S3` · `IAM` · `VPC` · `RDS` · `CloudWatch` · `AWS CLI`
