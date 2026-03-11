# Linux Networking Fundamentals

---

## Overview of Networking Fundamentals

Networking enables communication between systems over a network using IP addresses, ports, and protocols.  
Each system has:
- IP Address
- Subnet Mask
- Gateway --> Router
- DNS Server --> Domain Name Resolution

---

## Network Types and Protocols

### Network Types

| Type | Description |
|----|-------------|
| LAN | Local Area Network | --> Home/Office |
| MAN | Metropolitan Area Network | --> City |
| WAN | Wide Area Network | --> City/State/Country | --> Global |

## IP Address Classes (Classful Networking)
IPv4 addresses are divided into 5 classes: A, B, C, D, and E.
## IP Address Classes – Summary Table

| Class | First Octet Range | Default Subnet Mask | Purpose / Usage        | Networks  | Hosts per Network |
|-------|--------------------|----------------------|--------------------------|-----------|--------------------|
| **A** | 1 – 126            | 255.0.0.0            | Very large networks      | 128       | ~16 million        |
| **B** | 128 – 191          | 255.255.0.0          | Medium networks          | 16,384    | 65,534             |
| **C** | 192 – 223          | 255.255.255.0        | Small networks           | 2+ million| 254                |
| **D** | 224 – 239          | N/A                  | Multicast groups         | N/A       | N/A                |
| **E** | 240 – 255          | N/A                  | Experimental/Research    | N/A       | N/A                |

### Special Notes
- **0.x.x.x** → Reserved  
- **127.x.x.x** → Loopback (localhost)  

### private IP ranges 
```
Class A: 10.0.0.0 – 10.255.255.255 (CIDR: 10.0.0.0/8) - Used for large enterprise networks.
Class B: 172.16.0.0 – 172.31.255.255 (CIDR: 172.16.0.0/12) - Used for medium-sized networks.
Class C: 192.168.0.0 – 192.168.255.255 (CIDR: 192.168.0.0/16) - Common for home and small office routers.

```


  
### Protocols

| Protocol | Purpose |
|--------|--------|
| TCP | Reliable communication | --> Connection-oriented |
| UDP | Fast but unreliable | --> Connectionless |
| HTTP/HTTPS | Web communication | --> Secure |
| FTP | File transfer | --> Secure |
| SSH | Secure remote access | --> Encrypted |
| ICMP | Network diagnostics | --> Ping |

---

##  Using ifconfig and ip Commands

### View IP Details
```bash
ifconfig --> Linux/Mac
ip a 
ipconfig --> Windows
```
Check Network Interfaces
```bash
ifconfig
```
Check Public IP (Internet IP)
```bash
curl ifconfig.me
```


### Test Network Connectivity
```bash
ping google.com
```

---


## Verify Network Connectivity

```bash
ip a
ping google.com
```


## Topology
1. POINT-TO-POINT -- Direct connection between two devices. 
2. BUS -- All devices share a single communication line.
3. STAR -- All devices connect to a central hub.
4. RING -- Each device is connected to two others, forming a circle.
5. MESH -- Devices are interconnected, providing multiple paths for data.
6. HYBRID -- Combination of two or more topologies.
7. TREE -- It is arranged hierarchically,

## commands on linux networking
1. ifconfig : Display or configure network interfaces.
2. ip : Show/manipulate routing, devices, policy routing, and tunnels.
3. ping : Test connectivity to a host.
4. nslookup : Query DNS to obtain domain name or IP address mapping.
