# SIEM Investigation – Malicious File Alert

## Alert Overview

In this investigation, I analyzed a malicious file download attempt that was detected and blocked by the SIEM system.

---

## Alert Details

Event ID: 76
Event Time: Mar 14, 2021 – 07:15 PM
Rule: SOC137 – Malicious File/Script Download Attempt
Severity Level: Medium
Source IP Address: 172.16.17.37
Hostname: NicolasPRD
File Name: INVOICE PACKAGE LINK TO DOWNLOAD.docm
File Hash: f2d0c66b801244c059f636d08a474079
File Size: 16.66 KB
Device Action: Blocked

Screenshot: ![Alert Details](/SIEM-investigations/Malicious-File-Alert/screenshots/Detail-Info-Alert.png)

---

## Threat Intelligence – Hash Analysis

I analyzed the file hash using VirusTotal.

* The file was flagged as malicious by multiple security vendors
* This confirms that the document is weaponized, likely containing malicious macros

Screenshot: ![Alert Details](/SIEM-investigations/Malicious-File-Alert/screenshots/Virus-Total-Result.png)

---

## Endpoint Investigation

I investigated the endpoint associated with the alert (172.16.17.37) using the Endpoint Security page on LetsDefend platform.

* The last recorded activity on the endpoint was March 7, 2021
* The alert was generated on March 14, 2021

This time gap made it unreliable to depend solely on timestamp-based filtering.



* I identified two suspicious PowerShell commands in the terminal history
  screenshot: ![Alert Details](/SIEM-investigations/Malicious-File-Alert/screenshots/Obfuscated-Commands.png)
* The commands appeared obfuscated, indicating possible attacker activity
* There were no logs available after March 7, which may indicate logging gaps or endpoint inactivity

 The detailed command: https://github.com/user-attachments/assets/a620b130-30a3-424f-9452-540e7e01c97e

---

## Log and Network Investigation

I further analyzed logs from the log management system.

* I identified three related events from March 7, 2021
* I extracted the requested URLs from each event
* All URLs were confirmed malicious through VirusTotal analysis

### Observations:

* Various vendors flagged the Requested URLs as malicious from each event
* There were no logs from the endpoint after March 7, suggesting possible evasion or inactivity

Video Evidence: 2-Virus-Total-Results.mp4

---

## Analysis

Based on my investigation, this alert corresponds to a confirmed malicious document delivery attempt.


* The SIEM system successfully blocked the download attempt
* Historical activity shows signs of PowerShell abuse, which is commonly used in post-exploitation

Although the file was blocked at the time of the alert, prior activity suggests that the endpoint may have been exposed to earlier malicious behavior.

---

## Response Actions

* The malicious file download attempt was blocked by the SIEM system
* I proceeded to contain the affected endpoint as a precautionary measure
* The threat was handled in line with containment procedures, preventing further risk to the system

---

## Outcome

True Positive

The alert correctly identified a real malicious attempt, and appropriate defensive measures were successfully applied.

---

## Recommendations

1. Enable continuous and centralized endpoint logging to prevent visibility gaps
2. Restrict and monitor PowerShell usage, especially for obfuscated commands
3. Implement email filtering to block or sandbox macro-enabled attachments
4. Deploy endpoint detection and response (EDR) solutions for better visibility
5. Conduct user awareness training on phishing and malicious attachments

---

## Report Link

Full investigation report: `https://app.letsdefend.io/case-management/casedetail/alvine12w/76`

---

## Conclusion

The malicious file was successfully prevented from execution due to the SIEM blocking action. While no immediate compromise was observed during the alert, historical indicators suggest prior suspicious activity. Continuous monitoring and improved logging are recommended to enhance detection and response capabilities.

---
