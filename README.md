# CIP-B105-CS2-C11-26-DFIT-17300
## Network Forensics Case Study: Web Service Access Investigation

**Student:** Simon Friday Adeka  
**Reg No:** DFIT-17300  
**Course:** CIP-B105 Computer Incident Response & Digital Forensics  
**Case:** CS2-C11-26

---

### **1. CASE SUMMARY**
This investigation analyzes network packet evidence `dorm_capture.pcap` to determine:
1.  Which device accessed the web service `willselfdestruct.com`
2.  If packet evidence can identify the person responsible
3.  If the attributed person appears on the Chemistry 109 roster

**Key Finding:**  
Network activity to `136.160.215.15` originated from `IP 10.10.81.75` / `MAC 00:1b:17:00:0a:3a`.  
Due to TLS 1.3 encryption and shared network, user identity and message content could not be confirmed.

**Attribution Confidence: LOW**

---

### **2. REPOSITORY STRUCTURE**
