---
Title: SWS101 snort Journal
categories: [SWS101, Journal6]
tags: [SWS101]
---
## Snort 

Snort is a popular open-source network intrusion detection system (IDS) and intrusion prevention system (IPS) developed by Cisco. 

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

There are six DAQ modules available in Snort;

- Pcap: Default mode, known as Sniffer mode.
- Afpacket: Inline mode, known as IPS mode.
- Ipq: Inline mode on Linux by using Netfilter. It replaces the snort_inline patch.  
- Nfq: Inline mode on Linux.
- Ipfw: Inline on OpenBSD and FreeBSD by using divert sockets, with the pf and ipfw firewalls.
- Dump: Testing mode of inline and normalisation.

Some essential principles for working with Snort effectively and securely;
- Understanding Fundamentals: Mastering the basics of Snort, including its operation, rule creation, and usage, is indeed essential. Building a solid foundation ensures better comprehension and application of more advanced concepts later on.
- Incremental Rule Creation: Starting with simple rules and gradually adding complexity is a prudent approach. This method allows for easier troubleshooting and debugging, as errors can be identified more readily when changes are made incrementally.
- Leveraging Existing Rules: Utilizing existing rules whenever possible is a smart strategy. It saves time and effort and also ensures consistency with established best practices and community standards. Modification or enhancement of existing rules can be done judiciously to meet specific requirements.
- Backup Configuration Files: Creating backups before making changes is a crucial precautionary measure. This practice ensures that you have a fallback option in case something goes wrong during the modification process, helping to minimize downtime and potential data loss.
- Rule Management: Rather than deleting rules outright, commenting them out allows you to preserve them while temporarily disabling their functionality. This approach maintains a record of previous configurations and facilitates easier rule reactivation if needed in the future.
- Testing Before Deployment: Thoroughly testing newly created or modified rules in a controlled environment before deploying them to a production environment is paramount. This testing phase helps identify and rectify any issues or conflicts, ensuring that the rules operate as intended without disrupting network operations.

By adhering to these principles, network administrators can effectively manage and maintain Snort deployments, enhance security posture, and mitigate risks associated with network threats.