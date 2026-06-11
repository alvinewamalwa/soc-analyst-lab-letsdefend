# Endpoint Detection and Response (EDR) Investigation

This folder documents my practical investigation of Endpoint Detection and Response (EDR) functionality on the LetsDefend platform. The exercise focused on understanding endpoint monitoring, process analysis, containment actions, and IOC-based threat hunting.

## Overview of EDR

Endpoint Detection and Response (EDR), also known as Endpoint Threat Detection and Response (ETDR), is a security solution that provides continuous monitoring and analysis of endpoint activities. It collects real-time endpoint data and applies detection rules and automated response capabilities to identify and respond to suspicious behavior.

In this exercise, I used the EDR interface to investigate endpoint activity, analyze running processes, and identify potential malicious execution based on defined objectives.

## Containment Concept

Containment is a critical response action in EDR that involves isolating a compromised device from the network. The main purpose of containment is to prevent attackers from moving laterally within the network or communicating with external systems.

When a device is contained, it is isolated from both internal and external network traffic while still maintaining communication with the EDR platform. This allows security analysts to continue investigating the incident without losing visibility into the endpoint.

EDR solutions also allow threat hunting using Indicators of Compromise (IOCs) such as file hashes or file names. By searching for a known malicious hash across all endpoints, it is possible to determine whether other systems have been affected by the same threat.

## Objective 1: Process Investigation (Roberto Host)

The first objective required me to investigate a device with the hostname “Roberto” to determine the full command used to execute a “Ps1.hta” file, which is a malicious file.

I navigated through the list of running processes associated with the host and analyzed them individually. During this investigation, I identified the process associated with mshta.exe and reviewed its execution path and command-line arguments, which revealed the complete execution command. This clearly indicates that the host is compromised.

The relevant result is shown in the screenshot:
![EDR process analysis showing mshta.exe execution on host Roberto](/EDR-analysis/screenshots/EDR-analysis.png)

## Objective 2: Host Identification via IOC

The second objective required identifying the hostname of the device where a file named “nmap” with the hash value “83e0cfc95de1153d405e839e53d408f5” was executed.

I performed an IOC-based search using the hash value within the EDR platform. The search results returned the affected endpoint, allowing me to determine the hostname of the compromised device as EricProd.

The result is documented in the screenshot:
![EDR process analysis showing mshta.exe execution on host Roberto](/EDR-analysis/screenshots/hostname-EDR.png)

## Conclusion

This exercise improved my understanding of EDR functionality, including process investigation, endpoint visibility, and IOC-based threat hunting. I also gained practical experience in analyzing execution behavior, identifying malicious activity, and using containment concepts for incident response.
