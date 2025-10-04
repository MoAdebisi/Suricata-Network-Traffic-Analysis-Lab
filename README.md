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
### 1. Examine a Custom Rule
Displayed and analysed the existing rule using:
<img width="946" height="191" alt="Screenshot 2025-10-04 at 18 16 29" src="https://github.com/user-attachments/assets/68667f91-746c-4ee3-8bd1-afe157d7f7ad" />

Rule breakdown:
- Action: alert – triggers an alert when matched
- Protocol: http – focuses on HTTP traffic
- Flow: established,to_server – client-to-server communication
- Content: "GET" – looks for HTTP GET requests
- SID/REV: Unique rule identifiers

Result: This rule generates an alert whenever Suricata identifies an HTTP GET request originating from the internal network to an external destination.

### 2. Trigger a Custom Rule

Executed Suricata using the sample network traffic:
<img width="951" height="236" alt="Screenshot 2025-10-04 at 18 42 26" src="https://github.com/user-attachments/assets/5e1d2a0d-904f-43f5-aa26-b98356993b3f" />
Note: Before running Suricata, there were zero files in the /var/log/suricata directory. After running Suricata, we have four new files in the directory including the fast.log and eve.json files. These are logs that we will now examine.
<img width="944" height="124" alt="Screenshot 2025-10-04 at 18 47 35" src="https://github.com/user-attachments/assets/29ed17af-98a5-4ff8-b06a-fb3c57c5df76" />

Result: We see that the custom rule successfully triggered alerts from traffic in the pcap file.

### 3. Analyse Detailed Logs (eve.json)
   While fast.log provides basic logging and alerting, eve.json contains alot more data nd because it is stored in JSON format, it is much more useful for analysis and procession by other applications.
   
Displayed detailed Suricata logs:

<img width="943" height="284" alt="Screenshot 2025-10-04 at 18 54 15" src="https://github.com/user-attachments/assets/44ff9c22-f81a-42e7-af0e-d35d9af7dec4" 

  For better readability:
<img width="942" height="874" alt="Screenshot 2025-10-04 at 18 55 49" src="https://github.com/user-attachments/assets/6c655dd4-663d-44a6-8cd0-0144b991c860" />

This format is lot easier to read but now, we will use the jq command again to extract specific event data from the eve.json file:
<img width="949" height="86" alt="Screenshot 2025-10-04 at 18 58 27" src="https://github.com/user-attachments/assets/30bf1587-ed4d-4663-8ba7-3166ecd633bd" />
Here, we extracted the specified fields in the square brackets: timestamp, flow id, alert signature, protocol and destination IP address. 

Next, we will filter out all events using the flow id. This is a unique identifier that Suricata assigns to every network flow. This is a useful tool for correlating network traffic that belongs to the same network flow. 

<img width="896" height="726" alt="Screenshot 2025-10-04 at 19 06 16" src="https://github.com/user-attachments/assets/ebfea42b-a898-4da4-825d-f93c34b5c01b" />

Result: Analysed event correlation through flow_id, understanding how Suricata groups related traffic flows.

## Key Takeaways

- Developed practical experience with Suricata as a Network IDS.
- Gained confidence writing and testing custom Suricata rules.
- Understood how logs (fast.log & eve.json) can be leveraged for incident detection.
- Used jq to filter and format JSON logs for improved visibility.

## Conclusion

This project reinforced my understanding of network traffic monitoring, log analysis, and alert correlation, key components of a Security Operations Centre (SOC) environment.
It reflects my growing skill in threat detection and response — translating theoretical knowledge from the Google Cybersecurity Certificate into real-world practice.
  

