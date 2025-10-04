# Suricata-Network-Traffic-Analysis-Lab
Hands-on project from the Google Cybersecurity Certificate. Analysing alerts, logs, and custom rules in Suricata.

This project demonstrates my ability to work with Suricata, an open-source Intrusion Detection System (IDS), Intrusion Prevention System (IPS), and network monitoring tool.

The goal of this lab was to:
- Understand the composition and behaviour of Suricata rules
- Trigger custom alerts by analysing network traffic from a packet capture (pcap) file
- Interpret log outputs from fast.log and eve.json

By completing this, I gained hands-on experience in network traffic inspection, rule creation, and event correlation — core skills in network security monitoring (NSM) and blue team analysis.

## Scenario

As a security analyst, I was tasked to monitor network traffic within my organisation.
I used Suricata to:
- Examine existing detection rules
- Create and test a custom rule
- Analyse generated alerts from Suricata logs

## Tasks Performed
1. Examine a Custom Rule
Displayed and analysed the existing rule using:
<img width="946" height="191" alt="Screenshot 2025-10-04 at 18 16 29" src="https://github.com/user-attachments/assets/68667f91-746c-4ee3-8bd1-afe157d7f7ad" />

Rule breakdown:
- Action: alert – triggers an alert when matched
- Protocol: http – focuses on HTTP traffic
- Flow: established,to_server – client-to-server communication
- Content: "GET" – looks for HTTP GET requests
- SID/REV: Unique rule identifiers

Result: This rule generates an alert whenever Suricata identifies an HTTP GET request originating from the internal network to an external destination.

