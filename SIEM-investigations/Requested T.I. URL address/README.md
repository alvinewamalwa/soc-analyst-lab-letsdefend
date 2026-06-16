# EventID: 75 - SOC105: Requested T.I URL Address

## Overview

In this investigation, I analyzed a high-severity alert triggered by a requested URL from an endpoint within the network. The goal was to determine whether the URL posed a security risk or if the alert was a false positive.

---

## I. Alert Details

* **Event ID:** 75
* **Alert Name:** SOC105 - Requested T.I URL Address
* **Severity:** High
* **Action:** Allowed
* **Source:** MarksPhone

From the initial alert review, I noted that the connection was allowed despite being flagged as high severity, which required further validation.

**Screenshot:** `Alert-Details.png`

---

## II. Initial URL Analysis

I began by analyzing the requested URL using VirusTotal.

* The URL was flagged **only once** as phishing
* No strong consensus from multiple security vendors

Since VirusTotal results are not always definitive, especially with low detection rates, I treated this as **inconclusive** and proceeded with deeper investigation.

**Screenshot:** `Virus-Total-Results.png`

---

## III. Further Investigation

### a) Log Management Analysis

I analyzed the endpoint activity associated with IP address **10.15.15.12**.

* Multiple events were observed
* Only one event matched the **same date as the alert (March 07, 2021)**

I focused on this event for deeper inspection.

#### Findings:

* No connections to known **Command and Control (C2) servers**
* No suspicious or anomalous traffic patterns
* The same URL had already been analyzed and showed minimal risk

This indicated no clear signs of malicious communication.

**Screenshot:** `Events.png`

---

### b) Endpoint Security Analysis

Next, I examined the endpoint for any signs of compromise.

#### Findings:

* No suspicious running processes
* No abnormal browser activity
* No unusual terminal history

The endpoint showed **no indicators of compromise (IOCs)**.

**Screenshot:** `Endpoint-Analysis.png`

---

### c) URL Redirect Chain Analysis (WhereGoes)

To safely analyze the behavior of the URL without directly interacting with it, I used a redirect tracing tool(wheregoes.com).

The analysis revealed a **3-step redirect chain**:

---

#### Hop 1 — HTTP 301 (Permanent Redirect)

* The initial URL redirected immediately
* **HTTP 301** indicates a permanent redirection to a new location
* Inspection of the HTTP response body and associated metadata revealed no anomalies or obfuscated code.

**Screenshot:** `301-Redirect.png`

---

#### Hop 2 — HTTP 302 (Temporary Redirect)

* The request was routed through the **Yandex search engine infrastructure**
* **HTTP 302** indicates a temporary redirect
* Behavior observed was consistent with normal web routing
* A review of the payload and metadata at this stage showed standard routing behavior with no malicious artifacts.

**Screenshot:** `302-Redirect.png`

---

#### Hop 3 — HTTP 200 (OK)

* The final destination resolved successfully
* **HTTP 200** indicates the request was successful
* The page led to the official **Google Play Store** listing for *Tap Scanner*

I verified that:

* The application is a legitimate PDF scanning tool
* It has over **100M+ downloads**
* No signs of malicious intent or tampering were observed

**Screenshot:** `200-Redirect.png`

---

### HTTP Status Code Summary

* **200 (OK):** Request succeeded, content delivered normally
* **301 (Moved Permanently):** Resource permanently redirected
* **302 (Found):** Temporary redirection to another URL

---

## IV. Conclusion

Based on the investigation:

* No malicious payloads were identified
* No suspicious endpoint activity was observed
* The redirect chain terminated at a **trusted and verified platform**
* No evidence of phishing, exploitation, or command-and-control activity

I concluded that the URL is **benign**.

Therefore, I classified the alert as a **false positive**.

---

## V. Playbook Execution

I successfully completed the investigation playbook with:

* **100% Success Rate**
* **100% Score**

**Playbook Link:**
https://app.letsdefend.io/case-management/casedetail/alvine12w/75

---

## Final Note

This investigation demonstrates the importance of validating alerts beyond automated detections. Even high-severity alerts can result from legitimate activity, and thorough analysis is essential to avoid false positives while maintaining security integrity.





