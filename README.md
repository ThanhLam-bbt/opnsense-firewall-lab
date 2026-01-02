# OPNsense Firewall System with IDS/IPS & High Availability Load Balancing

![Network Topology](assets/topology_network.png)

## 📌 Introduction

This project demonstrates the deployment of a secure and high-performance network infrastructure using **OPNsense**. The system integrates **Suricata (IPS)** for intrusion prevention, **Unbound DNS** for web filtering, and **HAProxy** for Layer 7 Load Balancing with ACL and Rate Limiting capabilities.

## 🛠️ Technology Stack

- **Core System:** OPNsense Firewall (FreeBSD based).
- **Security:** Suricata (IDS/IPS), Unbound DNS (Blacklist Filtering).
- **Load Balancing:** HAProxy (Layer 7, Round Robin, Health Checks).
- **Environment:** VMware Workstation, Kali Linux (Attacker/Client), Python Web Server.
- **Testing Tools:** cURL, Apache Benchmark (ab), Wireshark.

## 🚀 Key Features Implemented

### 1. Web Access Control (DNS Filtering)

- Blocked access to restricted domains (e.g., social media, gambling sites) using **Unbound DNS**.
- **Result:** Client received `NXDOMAIN` when accessing blocked sites.

### 2. Intrusion Prevention System (IPS)

- Deployed **Suricata** in Inline mode on WAN interface.
- Successfully detected and dropped malicious traffic (tested with EICAR test file).
- **Result:** Connection dropped immediately; Alerts logged in OPNsense.

### 3. Load Balancing & High Availability

- Configured **HAProxy** with **Round Robin** algorithm.
- **Health Check:** Automatically detects offline backend servers (simulated failure) and routes traffic to the remaining active node.
- **Access Control List (ACL):** Blocked access to `/admin` path (HTTP 403 Forbidden).

### 4. DDoS Mitigation (Rate Limiting)

- Implemented **Stick-table** strategy in HAProxy.
- **Threshold:** Limit requests > 20 reqs / 10s per Source IP.
- **Result:** Excessive requests rejected with `HTTP 429 Too Many Requests`.

## 📸 Screenshots & Evidence

### Failover Demonstration

_(Place a screenshot or GIF here showing Server 1 going DOWN and Traffic moving to Server 2)_

### DDoS Attack Blocking

_(Place a screenshot of Apache Benchmark result showing Non-2xx responses)_

## 📂 Project Structure

- `/configs`: Configuration backups (Sanitized).
- `/scripts`: Python and HTML scripts used for Backend simulation.
- `/docs`: Detailed project documentation.

## 👨‍💻 Author

**Pham Thanh Lam** - [University of Information Technology - VNU-HCM]
