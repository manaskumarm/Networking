# Networking
🌐 Networking Fundamentals → Advanced (System Design Guide)

This guide covers essential networking concepts required for system design interviews, backend engineering, and cloud architecture.

<img width="3087" height="3999" alt="image" src="https://github.com/user-attachments/assets/99a2d6e0-a05a-48ce-91a0-7239b2e5e4d4" />


**📌 Table of Contents**
IP Addressing (Public vs Private)
CIDR Notation
Subnets
DNS (Deep Dive + Records)
NAT (Network Address Translation)
TCP/IP Basics
Ports & Sockets
Routing (High-Level)
Load Balancers
CDN Basics
Networking in Cloud (Azure/AWS concept overview)

📍 1. IP Addressing
An IP address uniquely identifies a device on a network.

🌍 Public IP
Accessible from the internet
Globally unique

Used for:
Websites
APIs
Load balancers

🔒 Private IP
Used inside internal networks (LAN/VNet)
Not reachable from internet

Used for:
Databases
Internal services

**IPv4 vs. IPv6**
IPv4: 32-bit address (e.g., 192.168.1.1). Limited to ~4.3 billion addresses (exhausted).
IPv6: 128-bit address (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334). Created to solve IPv4 exhaustion.

📍 2. CIDR (Classless Inter-Domain Routing)
CIDR defines IP range and network size. IP/Prefix -> 192.168.1.0/24

The Slash Notation (/n)The number after the slash represents the Network Prefix (how many bits are fixed).Formula: $2^{(32 - n)}$ gives the total number of IP addresses in the block.

🔹 Common CIDR ranges
CIDR	IPs
/24	256
/25	128
/26	64
/16	65,536

📍 3. Subnets
A subnet divides a larger network into smaller isolated networks.

Split into subnets:

10.0.1.0/24 → Web Tier
10.0.2.0/24 → App Tier
10.0.3.0/24 → DB Tier

In a cloud environment (AWS/Azure), you divide your network into:

Public Subnets: Resources with a route to an Internet Gateway (e.g., Load Balancers).

Private Subnets: Resources with no direct internet access (e.g., Databases, Internal APIs).

🔹 Why subnets?
Security isolation
Traffic control (NSG rules)
Better organization
Scalability

📍 4. DNS (Domain Name System)

DNS converts domain names → IP addresses.
Example:
google.com → 142.250.x.x

🔹 DNS Flow
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

🔹 DNS Records Types
🟢 A Record

Maps domain → IPv4

example.com → 1.2.3.4
🟣 AAAA Record

Maps domain → IPv6

🟡 CNAME Record

Alias to another domain

www.example.com → example.com
🔵 MX Record

Mail servers

example.com → mail.example.com
🟠 TXT Record

Verification / metadata
Used for:

SSL verification
Domain ownership
🔴 NS Record

Defines authoritative name servers

📍 5. NAT (Network Address Translation)
NAT allows multiple devices in a private network to share a single public IP address to communicate with the internet.

NAT Gateway: A managed service that allows instances in a private subnet to connect to the internet (for updates/patches) but prevents the internet from initiating a connection with those instances.

Security Benefit: It acts as a one-way valve for traffic.

🔹 Types of NAT
1. Static NAT

1 private IP ↔ 1 public IP

2. Dynamic NAT

Pool of public IPs shared dynamically

🔥 Used in:
Home routers
Cloud gateways
Firewalls

📍 6. TCP/IP Basics
🔹 TCP (Transmission Control Protocol)
Reliable
Connection-based
Uses handshake
3-way handshake:
SYN → SYN-ACK → ACK
🔹 IP (Internet Protocol)
Handles addressing and routing
Unreliable (no delivery guarantee)

📍 7. Ports & Sockets
🔹 Port
Identifies application on a machine
Examples:
80   → HTTP
443  → HTTPS
5432 → PostgreSQL
3306 → MySQL

🔹 Socket
Combination of:
IP + Port

Example:
10.0.0.4:443


📍 8. Routing (High-Level)

Routing determines path of packets across networks.
🔹 Protocol used:
Border Gateway Protocol (BGP)
Flow:
Device → Router → ISP → Backbone → Destination Network

📍 9. Load Balancers

Distribute traffic across servers.

🔹 Types
L4 Load Balancer (TCP/UDP)
L7 Load Balancer (HTTP/HTTPS)

🔹 Algorithms
Round Robin
Least Connections
IP Hash

📍 10. CDN (Content Delivery Network)

Caches content closer to users.

Example providers:

Cloudflare
Akamai
🔹 Benefits
Faster response
Reduced backend load
Global availability

📍 11. Networking in Cloud (System Design View)

Example architecture in Microsoft Azure:

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

