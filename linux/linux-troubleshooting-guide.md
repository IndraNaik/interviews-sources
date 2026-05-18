# Linux Troubleshooting Guide for DevOps Engineers

# CPU Troubleshooting

Commands:
```bash
top
htop
mpstat
```

Investigation:
- CPU spikes
- Runaway process
- Infinite loops
- High load average

---

# Memory Troubleshooting

Commands:
```bash
free -m
vmstat
```

Common Problems:
- Memory leaks
- OOM killer
- Swap exhaustion

---

# Disk Troubleshooting

Commands:
```bash
df -h
du -sh *
```

Issues:
- Log growth
- Orphaned files
- Docker image buildup

---

# Network Troubleshooting

Commands:
```bash
netstat -tulnp
ss -tulnp
ping
traceroute
```

---

# Process Troubleshooting

Commands:
```bash
ps -ef
lsof
```

---

# Service Failures

Commands:
```bash
systemctl status <service>
journalctl -xe
```

---

# Real Incident

## Scenario
Application randomly crashing.

### Root Cause
Disk full caused database corruption.

### Prevention
- Disk monitoring
- Log rotation
- Alerting
