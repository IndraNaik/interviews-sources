# Kubernetes Production Debugging Handbook

# Principal Engineer Mindset

Never debug Kubernetes by randomly running commands.

Always debug layer by layer:
1. User impact
2. Ingress
3. Service
4. Pod
5. Container
6. Node
7. Control plane
8. Infrastructure

---

# Standard Debugging Flow

## Step 1: Identify Blast Radius

Questions:
- Single pod affected?
- Single node affected?
- Entire namespace affected?
- Entire cluster affected?
- Regional outage?

Commands:
```bash
kubectl get pods -A
kubectl get nodes
kubectl top nodes
```

---

# Pod Debugging

## CrashLoopBackOff

### Root Causes
- Wrong environment variables
- Database connectivity failure
- Application crash
- OOMKilled
- Missing secrets
- Invalid startup command

### Debugging
```bash
kubectl logs <pod>
kubectl describe pod <pod>
```

### Principal Engineer Thinking
Always identify:
- First failure timestamp
- Last successful deployment
- Config changes
- Secret rotation events

---

# Service Debugging

## Service Not Reachable

### Validate Endpoints
```bash
kubectl get endpoints
```

### Common Causes
- Selector mismatch
- Readiness probe failing
- Pod not ready
- Wrong targetPort

---

# Ingress Debugging

## 502 / 504 Errors

### Validate
```bash
kubectl describe ingress
kubectl logs -n ingress-nginx <pod>
```

### Common Causes
- Backend unavailable
- TLS issues
- Timeout mismatch
- DNS propagation

---

# Node Debugging

## Node Not Ready

### Check
```bash
kubectl describe node <node>
```

### Root Causes
- Disk pressure
- Memory pressure
- Kubelet stopped
- Network plugin failure

---

# ETCD Issues

## Symptoms
- API latency
- Cluster instability
- Frequent leader election

### Validate
```bash
etcdctl endpoint health
```

---

# Real Production Incident

## Scenario
Application latency suddenly increased.

### Investigation Flow
1. Check ingress latency
2. Check pod CPU/memory
3. Check node pressure
4. Check database latency
5. Check DNS resolution
6. Check packet drops
7. Check recent deployments

### Root Cause
Memory leak causing OOM and pod recycling.

### Prevention
- Memory limits
- HPA
- Proper observability
- Canary deployments
