# SIEM Investigation – Phishing Alert Case (Event ID 257)

This folder documents a SOC investigation I performed on a phishing alert generated in the LetsDefend SIEM platform. The case involved analyzing a deceptive email, identifying malicious indicators, reviewing endpoint activity to determine potential compromise, and to deploy deploy countermeasures to stop additional compromises.

## Alert Overview

The alert was triggered by rule SOC282 – Phishing Alert: Deceptive Mail Detected.

I began the investigation by reviewing the full alert details to understand the context, including sender information, SMTP IP address, recipient, and email classification as shown below.

![Description](/SIEM-investigations/Phishing-Alert/screenshots/detailed-info-257.png)



## Email Investigation

I analyzed the email directly from the Email Security interface on Letsdefend platform by entering the sender's email address. It was sent to Felix and contained a phishing lure designed to appear legitimate.

I reviewed the sender email, subject line, and content in detail. The message used social engineering techniques, including urgency and reward-based deception.

A call-to-action button labeled “Redeem Now” was visible within the email content, encouraging the user to interact with the message.

The email also contained a password-protected ZIP attachment named “free-coffee.zip”, with the password provided as “infected”.

 ![Description](/SIEM-investigations/Phishing-Alert/screenshots/phishing-email-1.png)![Description](/SIEM-investigations/Phishing-Alert/screenshots/phishing-email-2.png)![Description](/SIEM-investigations/Phishing-Alert/screenshots/phishing-email-3.png)


I navigated to the Log Management tab and used the search functionality to filter on the log data and focused on entries relevant to this investigation. By searching for the host's IP address I could view the logs and network connections associated with the host. I analyzed the logs from the relevant time period.

By looking at the source and destination addresses as shown below, it can be seen that there is an outbound connection.
![Description](/SIEM-investigations/Phishing-Alert/screenshots/src-dest-addresses.png)
I went ahead and viewed the raw log of each given entry.




## Entry-1 Log: This log shows when Felix downloaded the email attachment.
![Description](/SIEM-investigations/Phishing-Alert/screenshots/entry1-log.png)







## Entry-2 Log: This log shows the Coffee.exe process communicates with a suspicious IP address through port 3451.
![Description](/SIEM-investigations/Phishing-Alert/screenshots/entry2-log.png)





## Entry-3 Log: Here the process fails to establish connection with IP address 127.0.0.1

![Description](/SIEM-investigations/Phishing-Alert/screenshots/entry3-log.png)





## Investigation Summary

I analyzed the attachment using a sandbox environment known as Hybrid Analysis and confirmed to be malicious. That alone determined that the alert is a true positive meaning that the alert is legitimate and requires further action.

I used Threat Intel to validate indicators associated with the file and infrastructure.

## Response Action
To prevent more hosts from being affected, I contained the user felix and the other host with IP address 37.120.233.226 and removed the malicious email from the user's mailbox, I also ensured that the sender address and associated domain are blocked at the email gateway to prevent further delivery attempts. I went ahead and searched for similar emails across the organization to identify potential exposure to other users and  scanned the affected host for any residual malicious files or artifacts by going through all the processes runned by the two affected hosts after opening the malicious file, fortunately all the processes were safe.



## My Playbook

After successfully investigating the alert and closing the case, I came up with my own playbook `https://app.letsdefend.io/case-management/casedetail/alvine12w/257` about the case.

## Playbook Note
The alert (Event ID 257) was triggered by rule SOC282 indicating a potential phishing email. Analysis of the email metadata shows that it originated from SMTP IP 103.80.134.63 with sender address free@coffeeshooop.com, which appears suspicious and potentially spoofed. I entered the sender's email address on the email security intercface and found the subject "Free Coffee Voucher" suggests a social engineering attempt to lure the recipient. I identified an attachment(freecoffee.zip) in the email, and it is evident that the user interacted with the malicious file by opening it causing password infection on the host. Based on the analysis, the alert is classified as a phishing attempt with a confirmed compromise of password infection. To prevent more hosts from being affected, I contained the user felix and the other host with IP address 37.120.233.226 and removed the malicious email from the user's mailbox, I also ensured that the sender address and associated domain are blocked at the email gateway to prevent further delivery attempts. I went ahead and searched for similar emails across the organization to identify potential exposure to other users and  scanned the affected host for any residual malicious files or artifacts by going through all the processes runned by the two affected hosts after opening the malicious file, fortunately all the processes were safe.



## Recommended Remediation

Following the investigation of the phishing alert (Event ID 257), the following remediation and response actions are recommended based on the findings.



### 1. Sender and Infrastructure Blocking

* Block the sender email address `free@coffeeshooop.com`
* Block or monitor the associated SMTP IP address `103.80.134.63` in security controls.
* Add indicators of compromise (IOCs) to threat intelligence and email filtering systems.

### 2. Endpoint Protection

* Ensure endpoint security tools are active and updated.
* Confirm that no malicious processes or persistence mechanisms exist on the system.

### 3. Threat Intelligence Actions

* Enrich the SMTP IP address and sender domain using threat intelligence platforms.
* Update internal detection rules based on observed phishing patterns and indicators.

### 4. User Awareness

* Inform the affected user about the phishing attempt.
* Conduct phishing awareness training focusing on social engineering techniques such as urgency and reward-based scams.

### 5. Monitoring and Detection Improvement

* Increase monitoring for similar phishing patterns, especially emails using reward-based lures.
* Update SIEM rules to detect similar attachments, domains, and behavioral indicators.
* Review logs for any related activity from the same IP or domain across the environment.

### Conclusion

These remediation steps ensure containment of the identified phishing attempt, reduce the risk of recurrence, and strengthen overall detection and response capabilities within the environment.

