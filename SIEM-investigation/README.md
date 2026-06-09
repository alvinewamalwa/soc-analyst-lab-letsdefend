# SIEM Investigation – Phishing Alert Case (Event ID 257)

This folder documents a SOC investigation performed on a phishing alert generated in the LetsDefend SIEM platform. The case involved analyzing a deceptive email, identifying malicious indicators, and reviewing endpoint activity to determine potential compromise.

## Alert Overview

The alert was triggered by rule SOC282 – Phishing Alert: Deceptive Mail Detected.

I began the investigation by reviewing the full alert details to understand the context, including sender information, SMTP IP address, recipient, and email classification as shown below.

![Description](/SIEM-investigation/screenshots/detailed-info-257.png)



## Email Investigation

I analyzed the email directly from the Email Security interface on Letsdefend platform by entering the sender's email address. It was sent to Felix and contained a phishing lure designed to appear legitimate.

I reviewed the sender email, subject line, and content in detail. The message used social engineering techniques, including urgency and reward-based deception.

A call-to-action button labeled “Redeem Now” was visible within the email content, encouraging the user to interact with the message.

The email also contained a password-protected ZIP attachment named “free-coffee.zip”, with the password provided as “infected”.

 ![Description](/SIEM-investigation/screenshots/phishing-email-1.png)![Description](/SIEM-investigation/screenshots/phishing-email-2.png)![Description](/SIEM-investigation/screenshots/phishing-email-3.png)



## Investigation Summary

I analyzed the attachment using a sandbox environment known as Hybrid Analysis and confirmed to be malicious.

I used Threat Intel to validate indicators associated with the file and infrastructure.


## Conclusion

The alert was confirmed as a phishing attempt involving a malicious attachment. The email was successfully delivered and compromised the user's system after it was opened. I contained the incident following the standard SOC procedures of LetsDefend to prevent other systems from being compromised.

My Playbook

After successfully investigating the alert and closing the case, I came up with my own playbook `https://app.letsdefend.io/case-management/casedetail/alvine12w/257` about the case.
Playbook Note
The alert (Event ID 257) was triggered by rule SOC282 indicating a potential phishing email. Analysis of the email metadata shows that it originated from SMTP IP 103.80.134.63 with sender address free@coffeeshooop.com, which appears suspicious and potentially spoofed. The subject "Free Coffee Voucher" suggests a social engineering attempt to lure the recipient. No URLs or attachments were identified in the email, and there is no evidence of user interaction or execution of malicious content on the host. Based on the analysis, the alert is classified as a phishing attempt with no confirmed compromise. Recommended actions include monitoring or blocking the sender address and performing further threat intelligence checks on the associated IP address.
