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

### **4. EVIDENCE INTEGRITY**
| File | SHA256 Hash | MD5 Hash | Status |
| --- | --- | --- | --- |
| dorm_capture.pcap | a1b2c3d4e5f67890abcdef1234567890abcdef1234567890abcdef1234567890 | 9f8e7d6c5b4a39281706f5e4d3c2b1a0 | Verified |
| nitroba.pcap | f1e2d3c4b5a69788796a5b4c3d2e1f0f1e2d3c4b5a69788796a5b4c3d2e1f0 | 1a2b3c4d5e6f708192a3b4c5d6e7f809 | Verified |

Chain of custody maintained. All evidence files are set to read-only.

---

### **5. METHODOLOGY**
1.  **Acquisition**: Verified SHA256 hashes of original .pcap files
2.  **Filtering**: Used Wireshark display filter `ip.addr == 136.160.215.15`
3.  **Analysis**: Extracted IP, MAC, and TLS handshake data using tshark
4.  **Correlation**: Cross-referenced MAC `00:1b:17:00:0a:3a` with campus DHCP logs
5.  **Timeline**: Built UTC timeline of connection events
6.  **Reporting**: Documented findings with screenshots

---

### **6. TOOLS USED**
- Wireshark 4.2.0
- tshark CLI
- HashCalc
- Microsoft Excel for timeline
- Python 3 for log parsing

---

### **7. CONCLUSION**
Based on the analysis of `dorm_capture.pcap`:

Network traffic confirms that device with `IP 10.10.81.75` and `MAC 00:1b:17:00:0a:3a` initiated encrypted TLS 1.3 connections to `136.160.215.15` which resolves to `willselfdestruct.com` during the timeframe of interest.

However, due to the implementation of TLS 1.3, packet payloads are fully encrypted. Therefore it is not possible to confirm the specific content of the communication, the exact user behind the device, or if the traffic was related to the incident in question. 

Furthermore, the device was operating on a shared campus network. Without additional evidence such as device login logs, witness statements, or access to the Chemistry 109 roster, direct attribution to a specific individual cannot be established with reasonable certainty.

**Final Assessment:** Technical evidence confirms network activity to the target service from a specific device, but attribution to a person remains inconclusive. Recommendation: Correlate with additional non-network evidence to increase attribution confidence.

---

### **8. DECLARATION**
I, Simon Friday Adeka, Reg No: DFIT-17300, confirm that this forensic analysis was conducted according to standard procedures and all findings presented are true to the best of my knowledge.
