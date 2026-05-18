# AWS Real-Time Troubleshooting Guide

# Principal Engineer Approach

Never assume AWS issue is only AWS.

Always isolate:
1. Application
2. OS
3. Networking
4. IAM
5. DNS
6. Load balancer
7. Cloud provider layer

---

# EC2 Not Reachable

## Validate
- Security Groups
- NACLs
- Route Tables
- Internet Gateway
- Public IP
- SSH service
- Disk utilization

Commands:
```bash
systemctl status sshd
sudo netstat -tulnp
```

---

# ALB 502 Errors

## Root Causes
- App not listening
- Health check failure
- Wrong target group
- TLS mismatch
- Security group issue

### Validate
```bash
curl localhost:8080
```

---

# RDS Latency

## Investigation
- CPU spikes
- Slow queries
- Lock contention
- Connection exhaustion
- Network latency

### Metrics
- FreeableMemory
- ReadIOPS
- WriteIOPS
- DatabaseConnections

---

# S3 Access Denied

## Validate
- IAM policy
- Bucket policy
- SCP restrictions
- KMS permissions

---

# IAM Troubleshooting

## Common Problems
- Explicit deny
- Missing assume role
- Wrong trust policy
- Session token expiry

---

# Real Production Incident

## Scenario
Application suddenly inaccessible.

### Root Cause
Security group modified during deployment.

### Prevention
- IaC enforcement
- Drift detection
- Change approval
- Immutable deployments
