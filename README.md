# Using-IPSec-Tunneling
# Assisted Live Lab: Using IPSec Tunneling

> CompTIA Security+ (SY0-701) | VPN | IPSec | Wireshark | Windows Server | Cryptography | Enterprise Infrastructure

## 📌 Overview

This lab demonstrates how to configure and validate an IPSec VPN tunnel between two Windows Server hosts using Local Security Policy.

Two IPSec configurations were implemented:

- Attempt Mode – Negotiates encryption but allows plaintext fallback.
- Required Mode – Requires encrypted communication and blocks unsecured traffic.

Wireshark was then used to compare network traffic before and after IPSec was enabled.

---

# 🎯 Objectives

- Configure IPSec Security Policies
- Create IP Filter Lists
- Configure Filter Actions
- Configure Pre-Shared Key Authentication
- Compare IPSec Attempt vs Required policies
- Capture network traffic with Wireshark
- Verify encrypted VPN communications
- Identify ISAKMP and ESP traffic
- Understand Layer 3 encryption

---

# 🖥️ Lab Environment

| Device | Role | IP Address |
|---------|------|------------|
| PC10 | Windows Server Client | 10.1.24.101 |
| PC20 | Windows Server Client | 10.1.24.102 |
| Router | Default Gateway | 10.1.24.254 |
| DVWA Server | Test Web Server | 172.16.0.201 |

---

# 🛠️ Technologies Used

- Windows Server 2019
- IPSec
- VPN
- ESP
- ISAKMP / IKE
- Wireshark
- PowerShell
- ICMP
- HTTP
- Local Security Policy

---

# ⚙️ Configuration Summary

## PC10 - IPSec Attempt Policy

Configured an IPSec policy that:

- Negotiates encrypted communications
- Allows fallback to unsecured traffic
- Uses Any IP Address
- Uses Any Protocol
- Uses Integrity + Encryption
- Uses a Pre-Shared Key
- Uses Transport Mode

---

## PC20 - IPSec Required Policy

Configured an IPSec policy that:

- Requires encrypted communication
- Blocks plaintext communication
- Uses the same authentication method
- Requires successful IPSec negotiation

---

# 🔍 Verification

### Before IPSec

- Ping successful
- HTTP traffic visible
- ICMP traffic visible
- Packets readable in Wireshark

### After IPSec

- Ping successful
- HTTP traffic to DVWA remained visible
- ICMP traffic between PC10 and PC20 disappeared
- ESP packets appeared
- ISAKMP negotiation packets appeared

This demonstrated that communication between the two hosts was encrypted.

---

# 🔬 Useful Wireshark Filters

```text
http
```

```text
icmp
```

```text
icmp.type!=3
```

```text
isakmp
```

```text
esp
```

```text
ip.addr==10.1.24.101
```

```text
ip.addr==10.1.24.102
```

---

# 🔐 IPSec Attempt vs Required

| Feature | Attempt Policy | Required Policy |
|---------|----------------|-----------------|
| Negotiates IPSec | ✅ | ✅ |
| Allows Plaintext Fallback | ✅ | ❌ |
| Requires Encryption | ❌ | ✅ |
| Production Ready | Limited | Yes |
| Security Level | Medium | High |

---

# 📚 Security Concepts

## IPSec

Provides authentication, integrity, and encryption for IP communications.

### ESP (Encapsulating Security Payload)

Provides:

- Encryption
- Authentication
- Integrity

Encrypts the packet payload.

### ISAKMP / IKE

Responsible for:

- Key exchange
- Security Association negotiation
- IPSec tunnel establishment

### Transport Mode

Encrypts only the payload while leaving the original IP header intact.

### Tunnel Mode

Encrypts the entire original IP packet inside a new packet.

### Pre-Shared Key (PSK)

Both hosts authenticate using the same shared secret before creating the VPN.

---

# 💼 SOC Analyst Skills Demonstrated

- VPN configuration
- IPSec policy deployment
- Packet capture analysis
- Wireshark investigation
- Enterprise network security
- Encryption verification
- ISAKMP negotiation analysis
- ESP packet identification
- Network troubleshooting
- Secure communications validation

---

# ✅ Key Takeaways

- IPSec protects traffic at OSI Layer 3.
- ESP encrypts network traffic.
- ISAKMP negotiates encryption keys.
- Attempt Mode allows plaintext fallback.
- Required Mode enforces encrypted communication.
- Wireshark can detect IPSec negotiations but cannot read encrypted payloads.
- IPSec significantly improves confidentiality for internal communications.

---

## ⭐ CompTIA Security+ Skills

- VPN Technologies
- IPSec
- Enterprise Infrastructure
- Cryptography
- Secure Communications
- Network Security
- Packet Analysis
- Wireshark
- Windows Security
- Security Operations
