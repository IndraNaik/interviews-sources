# Networking for DevOps Engineers

# Core Concepts

## OSI Layers
1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

---

# TCP vs UDP

| TCP | UDP |
|---|---|
| Reliable | Fast |
| Connection oriented | Connectionless |
| Ordered delivery | No ordering |

---

# DNS Debugging

Commands:
```bash
nslookup
host
dig
```

Common Issues:
- DNS propagation
- Wrong records
- TTL caching
- Resolver failure

---

# Load Balancing

## Types
- Round robin
- Least connections
- IP hash
- Weighted routing

---

# SSL/TLS Troubleshooting

## Common Problems
- Expired certificate
- Intermediate chain missing
- Cipher mismatch
- Hostname mismatch

Validate:
```bash
openssl s_client -connect domain.com:443
```

---

# Kubernetes Networking

## Important Concepts
- ClusterIP
- NodePort
- LoadBalancer
- Ingress
- CNI

---

# Real Incident

## Scenario
Pods healthy but traffic failing.

### Root Cause
CoreDNS failure.

### Investigation
```bash
kubectl logs -n kube-system -l k8s-app=kube-dns
```

### Prevention
- DNS monitoring
- Redundant replicas
- Node anti-affinity
