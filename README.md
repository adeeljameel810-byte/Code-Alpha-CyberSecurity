# 🔐 CodeAlpha Cybersecurity Internship Projects

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![GitHub](https://img.shields.io/badge/GitHub-adeeljameel810--byte-black?logo=github)](https://github.com/adeeljameel810-byte)
[![Status](https://img.shields.io/badge/Status-Active-success)](https://github.com/adeeljameel810-byte/Code-Alpha-CyberSecurity)

A comprehensive collection of **practical cybersecurity projects** developed during the CodeAlpha Internship. This repository focuses on real-world security concepts including network analysis, threat awareness, and intrusion detection.

---

## 👨‍💻 About

**Author:** Jameel Ahmed Khuhro  
**Department:** Software Engineering  
**Internship Program:** CodeAlpha  
**Focus Areas:** Network Security, Secure Coding, Cyber Awareness, Intrusion Detection

This repository demonstrates hands-on experience with cybersecurity tools, network protocols, and security best practices through practical implementations.

---

## 📂 Project Structure

```
Code-Alpha-CyberSecurity/
├── README.md                          # This file
├── LICENSE                            # MIT License
├── requirements.txt                   # Python dependencies
├── .gitignore                         # Git ignore rules
├── packet_sniffer.py                  # Network packet capture tool
├── network_ids_setup.md               # NIDS installation guide
├── phishing_awareness_module.md       # Phishing training content
└── security_audit_packet_sniffer.md   # Security audit documentation
```

---

## 🎯 Projects Overview

### 1. 🛰️ **Basic Network Packet Sniffer**
**File:** `packet_sniffer.py`

Captures and analyzes live network traffic with detailed packet inspection.

#### Features
- ✅ Capture live network packets in real-time
- ✅ Extract packet metadata:
  - Source & Destination IP addresses
  - Protocol types (TCP, UDP, ICMP)
  - Payload data with hex dump
- ✅ Flexible filtering (BPF filter expressions)
- ✅ Verbose mode for detailed analysis
- ✅ Fallback to raw sockets if Scapy unavailable

#### Technologies
- **Python 3.8+**
- **Scapy** - Powerful packet manipulation library
- **Socket Programming** - Raw socket fallback

#### Installation & Setup

```bash
# 1. Clone the repository
git clone https://github.com/adeeljameel810-byte/Code-Alpha-CyberSecurity.git
cd Code-Alpha-CyberSecurity

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. (Optional) Install additional tools for NIDS
sudo apt update
sudo apt install snort suricata
```

#### Usage

**Basic packet capture:**
```bash
# Capture packets on default interface
sudo python3 packet_sniffer.py

# Capture specific number of packets
sudo python3 packet_sniffer.py -c 10

# Capture on specific interface
sudo python3 packet_sniffer.py -i eth0 -c 20

# Verbose mode (shows payload data)
sudo python3 packet_sniffer.py -v -c 5

# Filter specific traffic (BPF filter)
sudo python3 packet_sniffer.py -f "tcp port 443" -v

# TCP traffic only
sudo python3 packet_sniffer.py -f "tcp" -c 15

# HTTP traffic analysis
sudo python3 packet_sniffer.py -f "tcp port 80" -v
```

#### Example Output
```
[2026-08-17 14:32:45] 192.168.1.100 -> 8.8.8.8 | TCP | IP / TCP 192.168.1.100:54321 > 8.8.8.8:443 S
Layers: IP, TCP
Payload length: 0 bytes
--------------------------------------------------------------------------------
[2026-08-17 14:32:46] 10.0.0.5 -> 192.168.1.1 | UDP | IP / UDP 10.0.0.5:53 > 192.168.1.1:53
Payload length: 45 bytes
```

#### Learning Outcomes
- 🎓 Deep understanding of OSI model layers
- 🎓 Network packet structure and protocols
- 🎓 Practical experience with Scapy library
- 🎓 Python socket programming

---

### 2. 🎣 **Phishing Awareness Training**
**File:** `phishing_awareness_module.md`

Educational module designed to identify and prevent phishing attacks.

#### Topics Covered
- 🎯 **Phishing Email Identification**
  - Suspicious sender addresses
  - Generic greetings and urgency tactics
  - Malicious links and attachments
  
- 🎯 **Fake Website Detection**
  - URL manipulation techniques
  - SSL certificate verification
  - Domain spoofing indicators
  
- 🎯 **Social Engineering Techniques**
  - Pretexting and baiting
  - Quid pro quo attacks
  - Tailgating and physical security
  
- 🎯 **Prevention & Best Practices**
  - Multi-factor authentication (MFA)
  - Password management strategies
  - Incident reporting procedures

#### Key Takeaways
✓ Recognize common phishing tactics  
✓ Verify website legitimacy  
✓ Report suspicious communications  
✓ Implement security awareness culture  

---

### 3. 🔍 **Secure Coding Review**
**File:** `security_audit_packet_sniffer.md`

Comprehensive security audit of the packet sniffer implementation.

#### Audit Findings
- **Input Validation Issues**
  - Command-line argument validation
  - Interface name safety checks
  
- **Common Vulnerabilities**
  - Hardcoded credentials risk
  - Error handling and exceptions
  - Permission management
  
- **Code Quality**
  - Function documentation
  - Error messages clarity
  - Resource cleanup

#### Recommendations
1. Implement comprehensive logging
2. Add configuration file support
3. Implement rate limiting for packet capture
4. Add output format options (JSON, CSV)
5. Enhance error messages with actionable guidance

---

### 4. 🛡️ **Network Intrusion Detection System (NIDS)**
**File:** `network_ids_setup.md`

Configuration and setup guide for enterprise-grade NIDS solutions.

#### Supported Tools
- **Snort** - Open-source IDS/IPS platform
- **Suricata** - High-performance network threat detection

#### Features
- 🔔 Real-time alert generation
- 📊 Network traffic logging
- 🎯 Custom detection rule creation
- 📈 Traffic analysis and statistics
- 🔐 Protocol anomaly detection

#### Setup Instructions

**Install Snort (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install snort

# Configure Snort
sudo nano /etc/snort/snort.conf

# Start monitoring
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
```

**Install Suricata (Ubuntu/Debian):**
```bash
sudo apt install suricata

# Update rules
sudo suricata-update

# Start Suricata service
sudo systemctl start suricata
sudo systemctl enable suricata

# Monitor alerts
sudo tail -f /var/log/suricata/eve.json
```

#### Custom Rule Example
```
alert tcp any any -> $EXTERNAL_NET 445 (msg:"SMB Exploitation Attempt"; \
  content:"|FF|SMB"; depth:4; offset:4; sid:1000001; rev:1;)
```

#### Learning Outcomes
- 🎓 Understanding of IDS/IPS architecture
- 🎓 Real-time network monitoring skills
- 🎓 Attack detection and response procedures
- 🎓 Log analysis and incident investigation

---

## 🛠️ Technologies & Tools

| Technology | Purpose |
|------------|---------|
| **Python 3.8+** | Main programming language |
| **Scapy** | Packet manipulation and analysis |
| **Snort** | Network intrusion detection |
| **Suricata** | Network threat detection |
| **Git/GitHub** | Version control |
| **Linux/Ubuntu** | Operating system |

---

## 📋 Requirements & Dependencies

### System Requirements
- **OS:** Linux (Ubuntu 18.04+) or macOS
- **Python:** 3.8 or higher
- **Privileges:** Administrator/root access for packet capture

### Python Dependencies
```bash
pip install -r requirements.txt
```

**requirements.txt:**
```
scapy>=2.4.5
```

### Optional Tools
```bash
# For NIDS setup
sudo apt install snort suricata

# For advanced traffic analysis
sudo apt install wireshark tshark
```

---

## ▶️ Quick Start Guide

### 1. Clone Repository
```bash
git clone https://github.com/adeeljameel810-byte/Code-Alpha-CyberSecurity.git
cd Code-Alpha-CyberSecurity
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run Packet Sniffer
```bash
# Basic usage (requires root)
sudo python3 packet_sniffer.py

# With options
sudo python3 packet_sniffer.py -i eth0 -c 10 -v
```

### 4. View Documentation
```bash
# Read NIDS setup guide
cat network_ids_setup.md

# Read phishing awareness content
cat phishing_awareness_module.md

# View security audit findings
cat security_audit_packet_sniffer.md
```

---

## 🎯 Key Skills Gained

| Skill | Application |
|-------|-------------|
| **Network Analysis** | Traffic capture and protocol analysis |
| **Security Awareness** | Phishing detection and prevention |
| **Secure Coding** | Vulnerability identification and fixes |
| **Intrusion Detection** | Real-time threat monitoring |
| **Linux Administration** | System configuration and management |
| **Python Programming** | Low-level network programming |

---

## 📊 Project Statistics

- **Total Projects:** 4
- **Main Language:** Python
- **Lines of Code:** 150+
- **Documentation:** Comprehensive
- **Difficulty Level:** Intermediate to Advanced

---

## 🔐 Security Best Practices

When using these tools:

1. **Legal Compliance**
   - ⚠️ Only capture traffic on networks you own or have explicit permission to monitor
   - ⚠️ Comply with local laws and regulations regarding network monitoring
   - ⚠️ Obtain proper authorization before running NIDS

2. **Responsible Use**
   - 🔒 Never use tools for unauthorized network access
   - 🔒 Protect sensitive data captured during analysis
   - 🔒 Report security findings responsibly

3. **Lab Environment**
   - 🧪 Practice in isolated lab networks first
   - 🧪 Use virtual machines for testing
   - 🧪 Document all activities and findings

---

## 📚 Additional Resources

### Cybersecurity Learning
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CIS Controls](https://www.cisecurity.org/controls/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)

### Tools Documentation
- [Scapy Documentation](https://scapy.readthedocs.io/)
- [Snort User Manual](https://www.snort.org/documents)
- [Suricata Documentation](https://suricata.readthedocs.io/)

### Network Protocols
- [RFC 791 - IP Protocol](https://tools.ietf.org/html/rfc791)
- [RFC 793 - TCP Protocol](https://tools.ietf.org/html/rfc793)
- [RFC 768 - UDP Protocol](https://tools.ietf.org/html/rfc768)

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/improvement`)
3. **Commit** your changes (`git commit -am 'Add improvement'`)
4. **Push** to the branch (`git push origin feature/improvement`)
5. **Open** a Pull Request

### Areas for Contribution
- 🔧 Additional packet analysis filters
- 📝 More comprehensive documentation
- 🛡️ Advanced NIDS rule sets
- 🐍 Performance optimizations
- 🧪 Unit tests and test cases

---

## 📝 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2026 Jameel Ahmed Khuhro

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.
```

---

## 🙏 Acknowledgments

- **CodeAlpha** - For providing this valuable internship opportunity
- **Open Source Community** - For tools like Scapy, Snort, and Suricata
- **Cybersecurity Professionals** - For guidance and best practices
- **Learning Resources** - OWASP, NIST, CIS, and security community

---

## 📞 Contact & Support

**Author:** Jameel Ahmed Khuhro  
**GitHub:** [@adeeljameel810-byte](https://github.com/adeeljameel810-byte)  
**Email:** Contact via GitHub profile

### Support
For issues, questions, or suggestions:
1. Open an [Issue](https://github.com/adeeljameel810-byte/Code-Alpha-CyberSecurity/issues)
2. Check existing documentation files
3. Review security audit findings

---

## ✅ Checklist for Using This Repository

- [ ] Read the entire README
- [ ] Review security best practices
- [ ] Install Python and dependencies
- [ ] Test packet sniffer in lab environment
- [ ] Review security audit findings
- [ ] Complete phishing awareness training
- [ ] Study NIDS setup guide
- [ ] Practice with filters and options
- [ ] Run tools with proper permissions
- [ ] Document your findings

---

**Last Updated:** August 2026  
**Status:** ✨ Active & Maintained  
**Version:** 1.0.0

---

<div align="center">

**Made with ❤️ for Cybersecurity**

</div>
