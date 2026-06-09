# Log Management Investigation

This folder documents my practical work on the LetsDefend Log Management interface. The objective of this exercise was to understand how logs from different sources are collected, correlated, analyzed, and visualized in a centralized environment.

## Overview

I used the Log Management section to perform targeted queries on system logs in order to extract specific security-relevant information. This exercise focused on improving my ability to filter logs and identify key indicators such as source IP addresses, destination ports, and log types.


## Objective 1: Identify Source IP Address

The first task required me to identify the source IP address that accessed a specific URL.

I used the log management interface to trace requests associated with the URL. Through this process, I was able to identify the originating IP address responsible for the activity.

The extracted result is shown in the screenshot below.

![Source IP Address Result](/Log-management/screenshots/IP-address.png)


## Objective 2: Identify Log Type by Destination Port

The second task required identifying the type of log associated with a destination port number of 52567 and a source IP address of 8.8.8.8.

I applied filtering techniques within the Log Management interface to narrow down relevant logs based on port and IP conditions. After analyzing the results, I determined the corresponding log type as shwon.

![DNS Log Result](/Log-management/screenshots/DNS.png)

## Conclusion

This exercise helped me understand how centralized log management systems operate in security monitoring environments. I gained practical experience in filtering logs, identifying network indicators, and correlating events based on specific criteria.

It improved my ability to perform basic log analysis tasks that are commonly used in SOC environments for threat detection and investigation.
