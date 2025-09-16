## Step-by-Step Guide: Analyzing Log Files in Splunk SIEM

### 1. **Understand What SIEM and Splunk Do**
- **SIEM (Security Information and Event Management)**: Collects, stores, and analyzes security data from multiple sources.
- **Splunk**: A powerful platform that indexes machine data and lets you search, visualize, and alert on it.

> _“Wise people think before they act.”_ — Proverbs 13:16 
**Reflection**: Before diving into logs, understand the purpose—detect threats, ensure accountability, and protect your digital environment.
---
### 2. **Identify Your Log Sources**
Common log sources include:
- **Windows Event Logs** (e.g., login attempts, system errors)
- **Linux Syslogs** (e.g., authentication, sudo usage)
- **Firewall Logs** (e.g., blocked traffic, port scans)
- **Web Server Logs** (e.g., access patterns, errors)

**Action**: Create a list of devices and services in your environment. Know what logs they generate.
---
### 3. **Ingest Logs into Splunk**
- Use **Universal Forwarder** or **Syslog** to send logs to Splunk.
- Configure **inputs.conf** and **props.conf** for proper parsing.
- Verify data is indexed correctly using:
  ```spl
  index=* | stats count by sourcetype
  ```
**Tip**: Start with a small dataset to practice before scaling up.
---
### 4. **Use Basic Search Queries**
Splunk uses its own query language called **SPL (Search Processing Language)**.

#### Example: Failed Login Attempts
```spl
index=security sourcetype=linux_secure "Failed password"
| stats count by src_ip
| where count > 5
```
**Explanation**:
- Searches for failed logins
- Groups by source IP
- Filters IPs with more than 5 failed attempts

> _“Stay alert! Watch out for your great enemy...”_ — 1 Peter 5:8 (NLT)  
**Reflection**: Repeated failed logins may signal a brute-force attack. Teach youth to recognize digital threats like spiritual ones—subtle but dangerous.
---
### 5. **Visualize with Dashboards**
- Create charts for login trends, blocked IPs, or system errors.
- Use **bar graphs**, **line charts**, and **heat maps** to make data accessible.

**Example Panel**:
```spl
index=security "Failed password"
| timechart count by src_ip
```
**Tip**: Use visuals to teach pattern recognition—great for youth workshops.
---
### 6. **Set Up Alerts**
- Define thresholds (e.g., >10 failed logins in 5 minutes)
- Configure email or SMS alerts
- Use **adaptive thresholds** for dynamic environments

**Example Alert Query**:
```spl
index=security "Failed password"
| stats count by user
| where count > 10
```
---
### 7. **Document and Reflect**
- Keep a log analysis journal
- Include:
  - Query used
  - What was discovered
  - Action taken
  - Biblical reflection or life lesson

> _“Let us examine our ways and test them...”_ — Lamentations 3:40 (NIV)
---
## Resources for Learners

| Resource Type         | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| [Splunk Fundamentals 1](https://www.splunk.com/en_us/training.html) | Free beginner course from Splunk |
| [SPL Cheat Sheet](https://docs.splunk.com/images/1/16/SPL_Cheat_Sheet.pdf) | Quick reference for search commands |
| [Try Splunk Cloud](https://www.splunk.com/en_us/download/splunk-cloud.html) | Free trial for hands-on practice |
| [MITRE ATT&CK Framework](https://attack.mitre.org/) | Understand tactics and techniques used by attackers |
| [BibleGateway](https://www.biblegateway.com/) | Source for full scripture references |

---

## Exercise
**Scenario**: A student notices their school computer is slow. You suspect malware.

**Task**:
- Search for unusual processes in logs
- Identify IP addresses communicating with the device
- Create a dashboard showing traffic volume by hour

**Discussion**:
- How does vigilance in cybersecurity mirror vigilance in life?
