# EC2 Hands-On: Launching Your First Instance

**Date:** May 2026  
**Region:** Europe (Stockholm) — `eu-north-1`  
**Account:** Neha MHATRE (967880486450)

---

## What I Did

Launched an EC2 instance from scratch using the AWS Console.

---

## Step-by-Step Process

### 1. Navigated to EC2 Console
- AWS Console → Search "EC2" → Instances → **Launch an instance**

---

### 2. Chose Amazon Machine Image (AMI)

- Initially selected **macOS Sequoia 15.7.5** (AMI ID: `ami-00f3fe7c423e50971`)
  - Architecture: 64-bit (Mac)
  - Publish Date: 2026-04-13
  - Verified provider ✅
- **Problem faced:** macOS AMI has `x86_64_mac` architecture — not compatible with standard instance types like `t3.micro`
- **Fix:** Switched AMI to **Amazon Linux 2023** (free tier eligible, `x86_64` architecture)

> **Lesson:** Always match AMI architecture with instance type. macOS instances require dedicated Mac hardware (very expensive, not free tier). For learning → always use Amazon Linux or Ubuntu.

---

### 3. Selected Instance Type

- Explored instance types: `t3.nano`, `t3.micro`, `t3.small`, `t3.medium`
- Selected **t3.micro** — Free tier eligible
  - Family: t3
  - vCPU: 2
  - Memory: 1 GiB
  - Current generation: true

> **What is t3.micro?** Burstable performance instance — good for low-traffic apps, learning, and small projects.

---

### 4. Configured Storage

- Volume: **1x 100 GiB**
- Type: **General Purpose SSD (gp3)** — Free tier eligible
- 3000 IOPS, Not encrypted
- Other options explored:
  - `gp2` — older SSD, also free tier
  - `io1/io2` — Provisioned IOPS, high performance (paid)
  - `sc1` — Cold HDD (not compatible with root volume)
  - `st1` — Throughput Optimized HDD (not compatible with root volume)
  - `standard` — Magnetic, legacy

> **Lesson:** For root volumes → always use `gp3` (better than `gp2`, same cost). `io1/io2` only when you need guaranteed high IOPS (databases).

---

### 5. Configured Key Pair

- Got a warning: *"You didn't select a key pair"*
- Selected: **Create new key pair**
  - Key pair type: **RSA**
  - Private key file format: **.pem** (for OpenSSH / Mac/Linux terminal)
  - `.ppk` is for PuTTY (Windows)
- Downloaded `.pem` file — **stored safely locally**

> **Critical:** Never push `.pem` file to GitHub. Add `*.pem` to `.gitignore`. If lost, you cannot SSH into the instance.

---

### 6. Launched the Instance

- Clicked **Launch instance**
- Result: ✅ **Success**
- Instance ID: `i-0964f84632e8a74ab`

---

### 7. Instance Summary

After launch, verified details:

| Field | Value |
|---|---|
| Instance ID | `i-0964f84632e8a74ab` |
| Instance State | ✅ Running |
| Instance Type | `t3.micro` |
| Public IPv4 | `13.60.202.183` |
| Private IPv4 | `172.31.39.243` |
| Public DNS | `ec2-13-60-202-183.eu-north-1.compute.amazonaws.com` |
| VPC ID | `vpc-0a0567cd598c52491` |
| Subnet ID | `subnet-0b7e0a94b6f9c60df` |
| Region | `eu-north-1` (Europe - Stockholm) |
| IAM Role | None assigned |
| IMDSv2 | Required |

---

## Key Concepts Learned

| Concept | What it means |
|---|---|
| **AMI** | Blueprint for your instance (OS + pre-installed software) |
| **Instance Type** | Hardware configuration (CPU, RAM) |
| **Key Pair** | SSH authentication — `.pem` = your password to login |
| **Security Group** | Firewall rules — controls what traffic in/out |
| **Public IP** | IP to access your instance from internet |
| **Private IP** | IP used internally within AWS VPC |
| **gp3** | Current-gen SSD storage, 3000 IOPS baseline |
| **t3.micro** | Free tier instance, 2 vCPU, 1 GiB RAM |

---

## Mistakes & Fixes

| Mistake | Fix |
|---|---|
| Selected macOS AMI | Not compatible with t3 family — switched to Amazon Linux |
| No key pair initially | Created RSA `.pem` key pair before launch |

---

## What's Next (To Do)

- [ ] SSH into the instance: `ssh -i "keypair.pem" ec2-user@13.60.202.183`
- [ ] Install Python / deploy a simple FastAPI app on EC2
- [ ] Attach an IAM role to the instance
- [ ] Set up Security Group rules (allow port 22 for SSH, 8000 for app)
- [ ] **STOP the instance when not in use** (free tier = 750 hrs/month — don't waste)
- [ ] Explore Elastic IP (static IP that doesn't change on restart)
