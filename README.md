# 🌐 Networking Fundamentals → Advanced (System Design Guide)

This guide covers essential networking concepts required for:
- System Design Interviews  
- Backend Engineering  
- Cloud Architecture  

---

## 📊 Architecture Overview

<img width="440" height="470" alt="image" src="https://github.com/user-attachments/assets/99a2d6e0-a05a-48ce-91a0-7239b2e5e4d4" />

---

## 📌 Table of Contents

1. IP Addressing (Public vs Private)  
2. CIDR Notation  
3. Subnets  
4. DNS (Deep Dive + Records)  
5. NAT (Network Address Translation)  
6. TCP/IP Basics  
7. Ports & Sockets  
8. Routing (High-Level)  
9. Load Balancers  
10. CDN Basics  
11. Networking in Cloud (Azure/AWS Overview)  

---

## 📍 1. IP Addressing

An IP address uniquely identifies a device on a network.

### 🌍 Public IP
- Accessible from the internet  
- Globally unique  

**Used for:**
- Websites  
- APIs  
- Load balancers  

### 🔒 Private IP
- Used inside internal networks (LAN/VNet)  
- Not reachable from the internet  

**Used for:**
- Databases  
- Internal services  

### 🔄 IPv4 vs IPv6

| Type | Description |
|------|------------|
| IPv4 | 32-bit (e.g., `192.168.1.1`) – ~4.3 billion addresses (exhausted) |
| IPv6 | 128-bit (e.g., `2001:db8::7334`) – solves exhaustion |

---

## 📍 2. CIDR (Classless Inter-Domain Routing)

CIDR defines IP range and network size.

Example: 192.168.1.0/24

- `/n` = number of fixed network bits  
- Formula:  

2^(32 - n)

→ Total number of IPs  

### 🔹 Common CIDR Ranges

| CIDR | IPs |
|------|-----|
| /24  | 256 |
| /25  | 128 |
| /26  | 64  |
| /16  | 65,536 |

---

## 📍 3. Subnets

A subnet divides a large network into smaller isolated networks.

### Example

10.0.1.0/24 → Web Tier
10.0.2.0/24 → App Tier
10.0.3.0/24 → DB Tier


### Cloud Subnets

- **Public Subnet**
  - Has route to Internet Gateway  
  - Example: Load Balancers  

- **Private Subnet**
  - No direct internet access  
  - Example: Databases, Internal APIs  

### 🔹 Why Subnets?

- Security isolation  
- Traffic control (NSG rules)  
- Better organization  
- Scalability  

---

## 📍 4. DNS (Domain Name System)

DNS converts domain names → IP addresses.
google.com → 142.250.x.x

### 🔹 DNS Flow


Browser
↓
Recursive Resolver (ISP)
↓
Root Server (.)
↓
TLD Server (.com)
↓
Authoritative DNS Server
↓
IP Address Returned


### 🔹 DNS Record Types

| Record | Purpose | Example |
|--------|--------|---------|
| A      | Domain → IPv4 | example.com → 1.2.3.4 |
| AAAA   | Domain → IPv6 | google.com -> 2607:f8b0 |
| CNAME  | Alias | www → example.com |
| MX     | Mail server | example.com → mail.example.com |
| TXT    | Metadata, DKIM / verification | SSL, ownership |
| NS     | Specifies the Authoritative Nameservers for a zone. | ns1.awsdns.com |

---

## 📍 5. NAT (Network Address Translation)

NAT allows multiple private devices to share a single public IP.

### 🧠 Key Concept
- Acts as a **one-way valve**
- Outbound allowed, inbound blocked (by default)

### 🔹 NAT Gateway
- Enables private subnet → internet access  
- Prevents inbound internet traffic  

### 🔹 Types of NAT

| Type | Description |
|------|------------|
| Static NAT | 1 private IP ↔ 1 public IP |
| Dynamic NAT | Pool of public IPs |

### 🔥 Used In
- Home routers  
- Cloud gateways  
- Firewalls  

---

## 📍 6. TCP/IP Basics

### 🔹 TCP (Transmission Control Protocol)
- Reliable  
- Connection-based  
- Uses handshake  

**3-way handshake:**

SYN → SYN-ACK → ACK

### 🔹 IP (Internet Protocol)
- Handles addressing & routing  
- Unreliable (no delivery guarantee)  

---

## 📍 7. Ports & Sockets

### 🔹 Port
Identifies an application on a machine.

| Port | Service |
|------|--------|
| 80   | HTTP |
| 443  | HTTPS |
| 5432 | PostgreSQL |
| 3306 | MySQL |

### 🔹 Socket

Socket = IP + Port
Example: 10.0.0.4:443


---

## 📍 8. Routing (High-Level)

Routing determines packet paths across networks.

### 🔹 Protocol
- BGP (Border Gateway Protocol)

### 🔹 Flow

Device → Router → ISP → Backbone → Destination Network


---

## 📍 9. Load Balancers

Distribute traffic across multiple servers.

### 🔹 Types

| Type | Layer |
|------|------|
| L4   | TCP/UDP |
| L7   | HTTP/HTTPS |

### 🔹 Algorithms

- Round Robin  
- Least Connections  
- IP Hash  

---

## 📍 10. CDN (Content Delivery Network)

Caches content closer to users.

### 🔹 Providers
- Cloudflare  
- Akamai  

### 🔹 Benefits

- Faster response  
- Reduced backend load  
- Global availability  

---

## 📍 11. Networking in Cloud (System Design View)

### Example Architecture (Azure)

User
↓
CDN
↓
Load Balancer
↓
API Gateway (APIM)
↓
App Tier (Subnet)
↓
Database (Private Subnet)


---

## 🚀 Final Notes

This guide is designed to:
- Build strong networking fundamentals  
- Help in system design interviews  
- Provide clarity for cloud architecture  

---





