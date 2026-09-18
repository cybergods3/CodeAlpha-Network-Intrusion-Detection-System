# CodeAlpha Network Intrusion Detection System

A Suricata based Network Intrusion Detection System (NIDS) project completed as part of my CodeAlpha Cybersecurity Internship Task 4.

---

## Project Overview

This project demonstrates the deployment and configuration of Suricata as a Network Intrusion Detection System (NIDS) on Ubuntu Linux.

The system was configured to:

- Monitor network traffic continuously
- Use detection rules to identify suspicious activity
- Generate security alerts
- Record detected events in EVE JSON format
- Monitor packet capture statistics
- Demonstrate a defensive response workflow

---

## Tools and Technologies

- Operating System: Ubuntu Linux
- Virtualization: Oracle VirtualBox
- IDS: Suricata 6.0.3
- Detection Mode: IDS using AF_PACKET
- Rule Source: Emerging Threats Open
- Log Format: EVE JSON
- Network Interface: enp0s3

---

## Suricata Service Status

The Suricata service was successfully started and verified.

The service was running in IDS mode using AF_PACKET.

Command used:

sudo systemctl status suricata --no-pager

The service status confirmed that Suricata was running successfully.

---

## Rule Configuration

The Emerging Threats Open rule set was updated using suricata-update.

Command used:

sudo suricata-update

The update process successfully:

- Loaded 68,635 rules
- Enabled 52,696 rules
- Enabled 136 flowbit dependency rules
- Updated the Suricata rule files
- Tested the Suricata configuration successfully

The configuration was also tested with:

sudo suricata -T

The rules were stored under:

/var/lib/suricata/rules/suricata.rules
---

## Continuous Network Monitoring

Suricata continuously monitored network traffic through the enp0s3 interface.

Packet capture statistics were checked using:

sudo grep -E 'capture.kernel_packets|capture.kernel_drops' /var/log/suricata/stats.log | tail -n 5
The `capture.kernel_packets counter increased during monitoring.

Observed values included:

- 4167
- 4177
- 4182
- 4190

The increasing packet counter demonstrated that Suricata was actively processing network traffic.

---

## Network Connectivity Testing

Network connectivity was verified using the following command:

ping -c 4 8.8.8.8

The test successfully returned responses from `8.8.8.8` with:

4 packets transmitted
4 received
0% packet loss

This confirmed that network connectivity was functioning during the laboratory test.

---

## Detection and Alert Logging

Suricata records detected security events in EVE JSON format.

The alert log was examined using:

sudo grep '"event_type":"alert"' /var/log/suricata/eve.json | tail -n 3

A previously captured alert included the signature:

GPL ICMP_INFO PING *NIX

The alert contained information such as:

- **Protocol:** ICMP
- **ICMP Type:** 8
- **Category:** Misc activity
- **Severity:** 3
- **Action:** allowed
- **Monitoring Interface:** `enp0s3`

---

## Evidence Note

The alert record available during the project review contained an older timestamp and older network addresses.

It is therefore documented as a **previously captured Suricata alert**, rather than a new alert from the current `10.226.95.0/24` laboratory network.

Normal network traffic does not necessarily generate an alert because an alert is only produced when traffic matches an enabled detection rule.

---

## Response Mechanism

The current Suricata deployment is configured as an **IDS**, rather than an inline IPS.

Therefore, the response process demonstrated by this project follows a defensive workflow:

Detect
   ↓
Alert
   ↓
Investigate
   ↓
Contain
   ↓
Continue Monitoring
`

### Response Workflow

#### 1. Detect

Suricata identifies network traffic matching a configured detection rule.

#### 2. Alert

The event is recorded in the EVE JSON log.

#### 3. Investigate

The analyst reviews information such as:

- Source IP
- Destination IP
- Protocol
- Port
- Alert signature
- Severity
- Timestamp

#### 4. Contain

If suspicious activity is confirmed, appropriate defensive controls such as host firewall rules or network isolation can be used to contain the activity.

#### 5. Continue Monitoring

Network activity continues to be monitored to determine whether the suspicious behavior has stopped.

> Automatic IPS blocking was not enabled for this project.

---

## Testing and Results

The following results were obtained during testing:

- Suricata was successfully installed and running.
- Suricata operated in IDS mode using AF_PACKET.
- The Emerging Threats Open rules were successfully updated.
- The Suricata configuration passed the configuration test.
- Network packet counters increased during monitoring.
- Suricata EVE JSON contained alert records.
- Network connectivity tests were successfully performed.
- Ordinary ping and web traffic did not necessarily generate new alerts because such traffic may not match the enabled detection rules.

---

## Evidence

The project documentation contains supporting evidence for the following:

| Evidence File | Description |
|---|---|
| suricata-service-running.png | Suricata service running in IDS mode |
| suricata-rules-updated.png | Suricata rules successfully updated and tested |
| suricata-packet-capture.png | Increasing packet capture statistics |
| suricata-alert-detection.png | Suricata alert recorded in EVE JSON |

---

## Project Structure

CodeAlpha Network Intrusion Detection System/
│
├── README.md
│
├── Task-4-Documentation.docx
│
├── Evidence/
│   ├── suricata-service-running.png
│   ├── suricata-rules-updated.png
│   ├── suricata-packet-capture.png
│   └── suricata-alert-detection.png
│
└── Configuration/
    └── suricata-config-notes.txt
---

## Conclusion

This project demonstrates the deployment of Suricata as a Network Intrusion Detection System on Ubuntu Linux.

The system was configured to monitor network traffic, use detection rules, record security events, and provide alerts for traffic matching those rules.

The project also demonstrates a practical defensive response workflow for investigating and containing suspicious network activity.

---

## CodeAlpha Internship

Program: CodeAlpha Cybersecurity Internship

Task: Task 4 – Network Intrusion Detection System

Project: Network Intrusion Detection System Using Suricata

GitHub Repository: CodeAlpha Network Intrusion Detection System

Internship ID: CA/DF1/262146

---

## Disclaimer

This project was performed in a controlled laboratory environment for educational and cybersecurity training purposes.
