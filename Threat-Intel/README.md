# Threat Intelligence Investigation

A Threat Intelligence Feed is data (such as malware hashes, C2 (Command&Control) domain/IP addresses etc.) provided by a third party company.



This folder documents my work with the Threat Intelligence interface on the LetsDefend platform. The objective of this exercise was to understand how threat intelligence feeds support SOC investigations and how to analyze indicators of compromise (IOCs).

## Overview

During this exercise, I familiarized myself with the Threat Intel interface, which aggregates various threat intelligence sources. This interface displays indicators of compromise such as malicious IP addresses, domains, file hashes, and URLs.

I learned how this centralized view helps SOC analysts quickly assess whether a given indicator is known to be malicious or associated with previous threats.

## Objective

The main objective was to identify the data source of the hash: `e1def6e8ab4b5bcb650037df234e2973` just so to improve my skills and the knowledge I already have.



I searched for this hash within the Threat Intel interface and identified its source as AbuseCH as shown below.

![Threat Intelligence result showing hash lookup and data source AbuseCH](/Threat-Intel/screenshots/Threat-Intel.png)

This demonstrated how threat intelligence feeds provide context about where and how an indicator has been observed.

## Understanding Threat Intelligence Feeds

I learned that a Threat Intelligence Feed is data provided by third-party organizations. This data includes indicators such as malware hashes, command-and-control (C2) IP addresses, and malicious domains.

These feeds are important because they allow SOC analysts to stay aware of emerging threats and take proactive measures during investigations.

## Key Lessons Learned

Through this exercise, I understood that threat intelligence should not be used blindly. If an indicator does not appear in threat intelligence platforms, it does not necessarily mean it is safe.

For example, a file hash that appears clean in VirusTotal may still be malicious. In such cases, I learned that I should perform deeper analysis, including static and dynamic analysis, rather than assuming the file is harmless.

I also learned that IP reputation must be interpreted carefully. IP addresses can change ownership over time. An IP address previously associated with malicious activity may later be reassigned for legitimate use. Therefore, historical reputation alone is not enough to determine current risk.

## Conclusion

This exercise helped me understand how to effectively use threat intelligence feeds in SOC investigations. I gained practical experience in identifying data sources, analyzing indicators, and applying critical thinking when evaluating threat intelligence results.
