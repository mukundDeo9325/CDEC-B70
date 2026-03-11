# Advanced Linux Process Management

---

## Understanding Process Priority and Nice Values

Linux assigns every process a **nice value** to decide its priority.

| Nice Value | Priority |
|-----------|---------|
| `-20` | Highest Priority |
| `0` | Default |
| `19` | Lowest Priority |

### Check Nice Value of a Process
```bash
top
```

---

## Finding Process IDs (PID)

| Command | Purpose |
|--------|--------|
| `ps aux` | Show all running processes |
| `pidof <process>` | Get PID of a process |

---

## Sending Signals to Processes

| Signal | Command | Purpose |
|------|------|------|
| SIGTERM (15) | `kill <pid>` | Graceful termination |
| SIGKILL (9) | `kill -9 <pid>` | Force kill |
| SIGHUP (1) | `kill -1 <pid>` | Kill all processes you can kill
|            | 'killall <processname>' | kill all the process by name | 
---

## Practical Example: Adjusting Priority of Long-Running Process

```bash
ps aux | grep nginx
renice 10 -p <PID>
```

---

## Overview of Process States

| State | Meaning |
|------|------|
| R | Running |
| S | Sleeping |
| D | Uninterruptible Sleep |
| Z | Zombie |
| T | Stopped |
| I | Idle |


```bash
ps -aux 
```

---

## Different Job Types and States

| Job State | Meaning |
|---------|--------|
| Foreground | Running on terminal |
| Background | Running with `&` |
| Stopped | Paused job |

Commands:
```bash
jobs
bg %1
fg %1
ctrl + Z # to stop the procss
```

---

## Visualizing The Process Tree

```bash
pstree
```
---

## Practical Example: Process Lifecycle Analysis

```bash
top
ps aux --sort=-%cpu | head
pstree
```

---
