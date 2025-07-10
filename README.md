# Phishing Email Analysis & IOC Extraction

## Project Overview

This repository contains a technical analysis of a suspicious email flagged by an organization’s email security gateway. The objective was to investigate the legitimacy of the email, uncover indicators of compromise (IOCs), and map findings to MITRE ATT&CK tactics. This project simulates a real-world phishing response scenario, including header analysis, authentication checks, sender verification, and IOC documentation.

---

## Actions Taken

### 1. Header & Email Path Analysis

I extracted and examined the full email header to identify the originating IP address and relay path. The email originated from `89.144.44.41`, which is not part of Microsoft’s infrastructure.

---

### 2. SPF, DKIM, and DMARC Authentication Checks

The email failed major authentication checks:

- **SPF**: No SPF record present (Result: None)
- **DKIM**: Signature missing (Result: None)
- **DMARC**: Permanent error in domain configuration (Result: permerror)

These failures are strong indicators of a spoofed or malicious email.

---

### 3. Sender Identity Verification

The email claimed to come from Microsoft:

`From: Microsoft account team <no-reply@access-accsecurity.com>`

But this domain is not affiliated with Microsoft. Additionally, the reply-to address was:

`Reply-To: solutionteamrecognizd03@gmail.com`

This mismatch confirmed spoofing.

---

### 4. X-Headers and Mail Relay Behavior

Reviewing Microsoft Exchange headers:

- `X-MS-Exchange-Organization-AuthAs: Anonymous`
- `X-MS-Exchange-Organization-AuthSource: MW2NAM04FT048.eop-NAM04.prod.protection.outlook.com`

These values show the message was accepted without authentication.

---

### 5. Timestamps & Delivery Path

The email passed through five mail servers without delay. While the timing seemed normal, the rapid delivery and unauthenticated origin reinforced suspicion.

---

### 6. IOC Extraction & MITRE Mapping

Extracted IOCs:

- IP Address: `89.144.44.41`
- Domains: `access-accsecurity.com`, `atujpdfghher.co.uk`
- Email Address: `solutionteamrecognizd03@gmail.com`

Mapped to MITRE ATT&CK Techniques:

- T1566.001 – Spearphishing via Email  
- T1585.001 – Spoofed Domain  
- T1110.003 – Credential Phishing

---

## Findings & Conclusion

The email was a phishing attempt impersonating Microsoft. Indicators include:

- Failed SPF, DKIM, and DMARC checks
- Mismatched display and reply-to addresses
- Anonymous relay behavior within Microsoft infrastructure

This project demonstrates my ability to identify and deconstruct phishing emails, extract relevant IOCs, and map findings to the MITRE ATT&CK framework. These techniques are essential for defending against email-based threats in real-world environments.

---

## Tools Used

- **MXToolbox** – DNS, SPF, and header analysis  
- **VirusTotal** – IOC verification  
- **Email Header Analyzer** – Header parsing  
- **MITRE ATT&CK Navigator** – Threat mapping


Received: from atujpdfghher.co.uk (89.144.44.41)

For screenshots and more details, refer to the Wiki page.
  (https://github.com/Deeoojo/Phishing-Email-Analysis-IOC-Extraction/wiki)
