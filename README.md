# Splunk SSH Log Analysis & Brute Force Detection Dashboard

This project demonstrates the creation of a specialized Splunk dashboard designed for real-time monitoring of SSH activity and the detection of potential brute force attacks against a Linux server. Using JSON-formatted SSH logs, I built a comprehensive view to help Security Operations Center (SOC) analysts quickly identify unauthorized access attempts, pinpoint targeted accounts, and visualize the geographic origins of attacks.

---
## The SSH Threat Dashboard

The final dashboard provides critical insights into SSH authentication patterns, highlighting anomalies and potential security threats at a glance. It serves as a primary tool for investigating credential access attempts and understanding the SSH attack surface.

<img src=".assets/Brute Force Dashboard.png" width="800" alt="Splunk dashboard showing SSH log analysis and brute force detection">
*<p align="center">Figure 1: The complete SSH Logs Dashboard, visualizing KPIs, targeted users, attack sources, and geographic locations.*</p>

---
## Dashboard & Panel Analysis

Each panel leverages specific Splunk Processing Language (SPL) queries to extract and visualize key security metrics from the raw SSH logs.

### 1. Authentication Overview KPIs
These panels provide an immediate summary of SSH traffic volume and success/failure rates.
* **Total SSH Events:** Overall activity baseline.
* **Successful Logins:** Tracks legitimate access. A sudden drop could indicate an availability issue.
* **Failed Logins:** A crucial indicator. Spikes often correlate with brute force or password spraying attacks.
* **Connection Without Authentication:** Tracks attempts using invalid usernames or other connection anomalies often seen during reconnaissance or misconfigured scans.

### 2. Login Activity Trends & Attack Indicators
These panels help identify specific targets and sources of malicious activity.
* **Failed Logins by Username:** This bar chart immediately highlights the most targeted accounts. In this case, `root` is the primary target, followed by common default or service account names, indicating likely automated attacks.
* **Possible Brute Force by IP Address:** This table isolates the source IPs responsible for multiple failed authentications, directly identifying potential attackers for blocking or further investigation. It includes the count and percentage of total failures attributed to each IP.

### 3. Geographic Visualization of Attacks
This choropleth map uses Splunk's `iplocation` and `geom` commands to plot the geographic origin of IPs associated with multiple failed authentications. This provides crucial context, helping analysts understand if attacks are targeted or part of global campaigns, and potentially informing firewall rule decisions. In this view, attacks are clearly originating from specific regions in North America and Asia.

---
##  Skills & Technologies Demonstrated

* **Splunk Enterprise:** Dashboard creation, data ingestion, panel configuration, and visualization.
* **Search Processing Language (SPL):** Writing queries using `stats`, `top`, `where`, `table`, `iplocation`, and `geom` for security event analysis.
* **Log Analysis:** Parsing and interpreting JSON-formatted SSH logs (`sshd`).
* **Threat Detection:** Identifying indicators of brute force attacks (failed logins, multiple attempts from single IPs).
* **Data Visualization:** Building intuitive dashboards to communicate security posture and active threats.
* **Cybersecurity Monitoring:** Applying SIEM skills to monitor critical access protocols like SSH.
