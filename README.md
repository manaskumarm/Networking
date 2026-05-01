# Networking
🌐 Networking Fundamentals → Advanced (System Design Guide)

This guide covers essential networking concepts required for system design interviews, backend engineering, and cloud architecture.

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

