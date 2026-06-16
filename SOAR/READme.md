# SOAR Familiarization

This folder documents my familiarization with Security Orchestration, Automation, and Response (SOAR) on the LetsDefend platform. The objective of this exercise was to understand how SOAR integrates security tools, automates workflows, and standardizes incident response processes within a SOC environment.

## Overview

During this exercise, I explored how SOAR enables different security tools and systems to work together efficiently. I learned that SOAR helps streamline the tasks of SOC analysts by automating repetitive processes and reducing manual effort.

For example, I observed how SOAR can automatically perform threat intelligence checks such as querying VirusTotal for an IP address associated with a SIEM alert. This significantly reduces the workload and allows analysts to focus on more complex investigation tasks.

## Automation and Time Efficiency

I learned that SOAR improves efficiency through automation by using predefined workflows. These workflows help perform common security tasks such as:

* IP address reputation checks
* Hash lookups
* File analysis using sandbox environments

This automation saves time and ensures that investigations are performed consistently and accurately.

## Centralization

I also understood that SOAR provides a centralized platform where multiple security tools can be accessed and used together. Instead of switching between different systems, analysts can perform investigations using integrated tools such as sandbox environments, log management systems, and third-party threat intelligence platforms within a single interface.

## Playbooks

One of the key features I explored was the use of playbooks. Playbooks provide step-by-step guidance for investigating different types of alerts and incidents.

I learned that playbooks help standardize the investigation process across the SOC team. By following predefined steps, analysts can ensure that critical checks, such as IP reputation analysis, are not missed.

Playbooks also improve collaboration and consistency, as all team members follow the same investigation procedures, reducing the risk of incomplete or inconsistent analysis.

## Below are playbooks that i have created after successfully investigating on the alerts

## i) phishing alert                                https://app.letsdefend.io/case-management/casedetail/alvine12w/257

## ii) malicious file alert                         https://app.letsdefend.io/case-management/casedetail/alvine12w/76

## iii) Requested T.I URL address investigation     https://app.letsdefend.io/case-management/casedetail/alvine12w/75  


## Conclusion

This exercise helped me understand how SOAR enhances SOC operations through automation, integration, and standardization. I gained insight into how workflows and playbooks can improve efficiency, reduce manual effort, and ensure consistent incident response across the team.
