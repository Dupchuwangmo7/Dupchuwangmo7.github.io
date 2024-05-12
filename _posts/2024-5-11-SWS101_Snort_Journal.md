---
Title: SWS101 snort Journal
categories: [SWS101, Journal6]
tags: [SWS101]
---
## Snort 

#### Intrusion Detection System (IDS)

IDS is a passive monitoring solution for detecting possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for generating alerts for each suspicious event. 

There are two main types of IDS systems;
- Network Intrusion Detection System (NIDS)
- Host-based Intrusion Detection System (HIDS)


#### Intrusion Prevention System (IPS)
IPS is an active protecting solution for preventing possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for stopping/preventing/terminating the suspicious event as soon as the detection is performed.

 There are four main types of IPS systems;
- Network Intrusion Prevention System (NIPS)
- Behaviour-based Intrusion Prevention System (Network Behaviour Analysis - NBA) 

Prevention Techniques
- Signature-Based
- Behaviour-Based
- Policy-Based	


## Points to be noted
- Packet Decoder - Packet collector component of Snort. It collects and prepares the packets for pre-processing. 

- Pre-processors - A component that arranges and modifies the packets for the detection engine.

- Detection Engine - The primary component that process, dissect and analyse the packets by applying the rules. 

- Logging and Alerting - Log and alert generation component.

- Outputs and Plugins - Output integration modules (i.e. alerts to syslog/mysql) and additional plugin (rule management detection plugins) support is done with this component. 

There are three types of rules available for snort
- Community Rules - Free ruleset under the GPLv2. Publicly accessible, no need for registration.
- Registered Rules - Free ruleset (requires registration). This ruleset contains subscriber rules with 30 days delay.
- Subscriber Rules (Paid) - Paid ruleset (requires subscription). This ruleset is the main ruleset and is updated twice a week (Tuesdays and Thursdays).
