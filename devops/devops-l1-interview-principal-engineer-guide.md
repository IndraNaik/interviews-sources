# DevOps L1 Interview Questions & Principal Engineer Answers

## Introduction & Project Experience

### 1. Self Introduction and Explain Your Project Work

Hi, I’m P Indra Naik. I have experience working as a Java Developer and AWS Cloud/DevOps Engineer. My primary focus has been on cloud infrastructure, CI/CD automation, containerization, Kubernetes, Terraform, and production troubleshooting.

In my projects, I worked on:
- AWS infrastructure provisioning using Terraform
- CI/CD pipelines using Jenkins and GitLab CI/CD
- Containerizing Java applications using Docker
- Kubernetes deployments with autoscaling and ingress
- Monitoring and troubleshooting production issues
- IAM and security configurations
- Infrastructure automation and state management

---

# Kubernetes

## 2. Define Pod Lifecycle

A Pod lifecycle defines the different phases a Kubernetes Pod goes through from creation to termination.

### Main Phases
1. Pending
2. Running
3. Succeeded
4. Failed
5. Unknown

### Important Production Concepts
- CrashLoopBackOff
- Init containers
- Readiness probes
- Liveness probes
- Restart policies

---

## 3. Describe Kubernetes Architecture

### Control Plane Components
- API Server
- ETCD
- Scheduler
- Controller Manager
- Cloud Controller Manager

### Worker Node Components
- Kubelet
- Kube Proxy
- Container Runtime

### Flow
kubectl apply → API Server → ETCD → Scheduler → Kubelet → Container runtime starts pod.

---

## 4. Difference Between Deployment and StatefulSet

| Feature | Deployment | StatefulSet |
|---|---|---|
| Used for | Stateless apps | Stateful apps |
| Pod names | Random | Stable |
| Storage | Shared/ephemeral | Persistent |
| Identity | Dynamic | Fixed |
| Scaling | Easy | Ordered |
| Example | Web app | MySQL, Kafka |

---

## 5. Difference Between PV and PVC

### Persistent Volume (PV)
Actual storage resource.

### Persistent Volume Claim (PVC)
Storage request made by applications.

---

## 6. Which is Static and Which is Dynamic?

- PV = Static resource
- PVC + StorageClass = Dynamic provisioning

---

## 7. Difference Between Ingress Controller and Load Balancer

| Feature | Ingress | Load Balancer |
|---|---|---|
| Layer | L7 | L4 |
| Routing | Host/path-based | Port-based |
| Cost | Lower | Higher |
| SSL termination | Yes | Limited |
| Multiple services | Yes | Usually no |

---

# Git & Version Control

## 8. Difference Between git pull and git fetch

### git fetch
Downloads changes only.

### git pull
Fetch + merge.

---

## 9. Snapshot Version vs Release Version

### Snapshot
Development build.
Example: 1.0-SNAPSHOT

### Release
Stable immutable version.
Example: 1.0.0

---

# Terraform

## 10. What is Terraform?

Terraform is an Infrastructure as Code (IaC) tool used to provision and manage infrastructure declaratively.

---

## 11. What is a State File?

Terraform state file tracks real infrastructure resources.

File:
terraform.tfstate

---

## 12. Recover Corrupted Terraform State File

### Recovery Steps
1. Restore backup state
2. Use remote backend versioning
3. Use terraform refresh
4. Import missing resources
5. Restore from S3 versioning

---

## 13. Difference Between for_each and count

| count | for_each |
|---|---|
| Index based | Key based |
| Good for identical resources | Good for unique resources |
| Less stable | More stable |

---

## 14. Types of Terraform Modules

1. Root Module
2. Child Module
3. Public/Remote Module

---

## 15. What is State Locking?

State locking prevents multiple users from modifying infrastructure simultaneously.

AWS Example:
- S3 for backend
- DynamoDB for locking

---

# Docker

## 16. What is Docker?

Docker is a containerization platform used to package applications with dependencies into lightweight portable containers.

---

## 16.1 Dockerfile for Java Application

```dockerfile
FROM openjdk:17-jdk-slim

WORKDIR /app

COPY target/app.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
```

---

## 17. Types of Networking in Docker

1. Bridge
2. Host
3. None
4. Overlay
5. Macvlan

---

## 18. Difference Between COPY and ADD

| COPY | ADD |
|---|---|
| Simple copy | Extra features |
| Preferred | Less predictable |
| No extraction | Can auto extract tar |

---

# AWS & Cloud

## 19. What is AWS?

AWS is a cloud computing platform providing compute, storage, networking, database, and security services.

---

## 19.1 What is IAM?

IAM controls authentication and authorization in AWS.

### IAM Components
- Users
- Groups
- Roles
- Policies

### IAM Roles
1. EC2 Role
2. Lambda Role
3. Cross-account Role
4. Service-linked Role

---

## 20. Types of Load Balancers in AWS

1. Application Load Balancer (ALB)
2. Network Load Balancer (NLB)
3. Gateway Load Balancer
4. Classic Load Balancer

---

## 21. Maximum Size of S3 Object

Maximum object size: 5 TB

Multipart upload required above 5 GB.

---

# Jenkins & CI/CD

## 22. Various Pipeline Stages in Jenkins

1. Checkout
2. Build
3. Unit Test
4. Static Code Analysis
5. Docker Build
6. Push Image
7. Deploy
8. Integration Testing
9. Notifications

---

# Troubleshooting & Real-Time Scenarios

## 23. Application Running But Not Accessible Publicly

### Troubleshooting Flow

#### Step 1: Check Application
```bash
netstat -tulnp
```

#### Step 2: Check Container
```bash
docker ps
docker logs <container>
```

#### Step 3: Check Kubernetes Service
```bash
kubectl get svc
kubectl describe svc
```

#### Step 4: Check Ingress
```bash
kubectl get ingress
```

#### Step 5: Check Security Groups
- Port open?
- Source allowed?

#### Step 6: Check NACLs and Firewall

#### Step 7: Check DNS

#### Step 8: Test Locally
```bash
curl localhost:8080
```

#### Step 9: Check Load Balancer Health Checks

#### Step 10: Trace Full Network Path

---

## 24. EC2 Instance Not Accessible

### Step-by-Step Debugging

#### Step 1: Check Instance Status
- Running?
- Status checks passed?

#### Step 2: Check Security Group
- SSH 22 open?
- Correct source IP?

#### Step 3: Check NACL

#### Step 4: Check Public IP

#### Step 5: Check Route Table and Internet Gateway

#### Step 6: Verify SSH Key

#### Step 7: Check OS Firewall
```bash
sudo ufw status
```

#### Step 8: Check SSH Service
```bash
systemctl status sshd
```

#### Step 9: Check Disk Space
```bash
df -h
```

#### Step 10: Check CPU and Memory Utilization

---

# Principal Engineer Mindset

Strong DevOps engineers are evaluated on:
- Debugging sequence
- Layered thinking
- Production awareness
- Failure isolation
- Risk understanding
- Real incident handling

### Standard Troubleshooting Pattern
1. Identify layer
2. Validate assumptions
3. Narrow blast radius
4. Verify logs and metrics
5. Fix root cause
6. Prevent recurrence
