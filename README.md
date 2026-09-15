Say less Simon 🔥 
Here’s your *complete GitHub README.md* for the repo. Copy-paste this as `README.md` in the root of `CIP-B105-CS2_C11-26-DFIT-17300_Simon/`

---

### *README.md*
# CIP-B105-CS2 | Network Forensics Investigation: Lily Tuckrige Harassment Case

**Student:** Simon  
**Reg No:** C11-26-DFIT-17300  
**Course:** CIP-B105 Digital Forensics  
**Date:** 2026-09-12  

## 1. CASE OVERVIEW
Lily Tuckrige reported receiving harassing emails. The first email header traced to a shared student-accommodation IP. A subsequent message referenced `willselfdestruct.com`. 

This investigation analyzes `dorm_capture.pcap` to determine:
1.  Which device accessed the web service
2.  If packet evidence can identify the person responsible
3.  If the attributed person appears on the Chemistry 109 roster

**Key Finding:** Network activity to `136.160.215.15` originated from `IP 10.10.81.75` / `MAC 00:1b:17:00:0a:30`. Due to TLS 1.3 encryption and shared network, user identity and message content could not be confirmed.  
**Attribution Confidence: LOW**

## 2. REPOSITORY STRUCTURE
CIP-B105-CS2_C11-26-DFIT-17300_Simon/
│
├── 01_Evidence/                    # Original read-only evidence
│   ├── dorm_capture.pcap           # Primary network capture
│   └── nitroba.pcap                # Reference capture
│
├── 02_Deliverables/                # Final submission files
│   ├── CIP-B105-CS2_RegNo_Simon.pdf    # Final forensic report
│   └── CIP-B105-CS2_RegNo_Simon.zip    # Submission package
│
├── 03_Working/                     # Analysis outputs
│   ├── capture_summary.txt         # Hashes, timeline, matrix, register
│   ├── Fig1_Evidence_Hash.png      # SHA256 of dorm_capture.pcap
│   ├── Fig2_Conversation_Analysis.png  # IP conversation table
│   ├── Fig3_MAC_Attribution.png    # MAC to IP attribution
│   ├── Fig4_Reference_Hash.png     # SHA256 of nitroba.pcap
│   ├── Fig5_UTC_Timeline.png       # UTC timestamps of incident
│   └── Fig6_Evidence_Register.png  # Evidence register + matrix
│
└── README.md                       # This file

## 3. EVIDENCE INTEGRITY
All evidence hashed using SHA256 prior to analysis.

| Evidence ID | File | SHA256 |
| --- | --- | --- |
| E001 | dorm_capture.pcap | `411989f35b6f60f97ea48935b115392547a54ce9372b8c1a03314679253f77` |
| R001 | nitroba.pcap | `2b7a9aeafc1d6af163d1ba793c96dbccab0e4ebefdf1a0b01f8c67553ec2fb` |
| S001 | Submission.zip | `54b1a46fc9a8618a5f3b5a16bafddd33d066426807a27e179d5c8f976b25348` |

[See Fig 1: Evidence Hash] [See Fig 4: Reference Hash]

## 4. METHODOLOGY & TOOLS
**Tools:** `tshark 4.x`, `sha256sum`, Oracle VirtualBox  
**Process:** 
1.  Hash Verification
2.  Conversation Analysis to find WEB_IP
3.  MAC to IP Attribution
4.  Protocol Analysis for TLS/HTTP
5.  Identity/Cookie Search
6.  Timeline Reconstruction
7.  Limitation & Confidence Assessment

## 5. KEY FINDINGS
### 5.1 Network Attribution
- **Suspect Device:** `MAC: 00:1b:17:00:0a:30` → `IP: 10.10.81.75` [See Fig 3]
- **Web Server:** `IP: 136.160.215.15` [Presumed willselfdestruct.com]
- **Traffic:** 10 frames, 13,810 bytes, 100% TLS [See Fig 2]

### 5.2 Content & Identity
- **POST Data:** NOT RECOVERABLE - TLS 1.3 encryption
- **Cookies/Email:** NOT RECOVERABLE - No plaintext HTTP
- **Roster Match:** NOT VERIFIED - Roster not provided

### 5.3 Timeline UTC
Incident occurred: `2023-02-02T14:29:56 UTC` [See Fig 5]

### 5.4 Attribution Matrix
[See Fig 6 for full matrix]
`MAC 00:1b:17:00:0a:30` → `IP 10.10.81.75` → `WEB 136.160.215.15` → `Identity: UNKNOWN`

## 6. LIMITATIONS
1.  **Encryption:** TLS prevents recovery of POST, SNI, Cookies
2.  **Shared Network:** Device could be used by multiple students
3.  **No Host Data:** Cannot confirm who operated the device
4.  **No Roster:** Cannot correlate to Chemistry 109

## 7. CONCLUSION
Packet evidence confirms device `MAC 00:1b:17:00:0a:30` communicated with the target web server. However, due to encryption and shared network architecture, specific user attribution and message content cannot be confirmed from network data alone.

**Recommendation:** Host-level forensic analysis of device `00:1b:17:00:0a:30` and provision of Chemistry 109 roster required for further attribution.

## 8. COMMANDS USED
```bash
# Hash Verification
sha256sum dorm_capture.pcap
sha256sum nitroba.pcap

# Conversation and IP Analysis
tshark -r dorm_capture.pcap -q -z conv,ip

# MAC Attribution
tshark -r dorm_capture.pcap -Y "ip.src == 10.10.81.75" -T fields -e eth.src

# Timeline Extraction
tshark -r dorm_capture.pcap -Y "ip.dst == 136.160.215.15" -T fields -e frame.number -e frame.time_utc

# Identity Search
tshark -r dorm_capture.pcap -Y "ip.src == 10.10.81.75" -T fields -e http.cookie -e http.user_agent
## 9. SUBMISSION
*Report:* `02_Deliverables/CIP-B105-CS2_RegNo_Simon.pdf`  
*Evidence Package:* `02_Deliverables/CIP-B105-CS2_RegNo_Simon.zip`

---
_This investigation was conducted in accordance with ACPO and NIST Digital Forensics guidelines._

---

### **HOW TO MAKE THE GITHUB REPO COMPLETE SIMON**

1.  **Create repo on GitHub:** `CIP-B105-CS2_C11-26-DFIT-17300_Simon`
2.  **Upload the 3 folders:** `01_Evidence`, `02_Deliverables`, `03_Working`
3.  **Add this README.md** to root
4.  **Add a .gitignore** so you don't push huge pcaps if repo limit:
_.pcap
    _.zip
    And put a note: "Evidence available on request due to file size"

Want me to also write you a `SUBMISSION_CHECKLIST.md` to go with it? 

This README will make you look like a pro forensic analyst bro 💪
