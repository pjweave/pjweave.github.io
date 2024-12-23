---
layout: page
title: Incident response
permalink: /incident/
---
![Datacentre surveillance][irhimg]

The [NIST SP 800-61r2 computer security incident handling guide][irl] defines the incident response life cycle that underpins the Security+ incident response subject matter and many other cybersecurity curricula. The life cycle is depicted as a multi-phase, cyclical process that should commence with a preparation phase, culminating in a post-incident activity, essentially a reflection on the lessons learned from the incident to improve future incident response efforts.

![NIST incident response life cycle][irlimg]

[irl]: https://doi.org/10.6028/NIST.SP.800-61r2
[irlimg]: /images/800-61r2-irl.bmp "NIST incident response life cycle"
[irhimg]: /images/incident%20response.jpg "Datacentre surveillance"

## Identification 
Use the following sources to help identify an incident: 

1. IDS/IPS 
2. Firewalls 
3. Authentication systems 
4. Integrity monitors 
5. Vulnerability scanners 
6. System event logs 
7. NetFlow records 
8. Anti-malware packages 

All can be collected and corelated in a SIEM (Security Incident and Event Management). 

Some incidents may be reported by external sources (customers etc.) 

Once identified, <b>first responders</b> must act quickly and isolate affected systems. The highest priority of a first responder must be containing the damage through isolation. 

Strategic intelligence programs facilitate incident identification efforts. 

Counterintelligence hinders adversary abilities to gather intelligence. 

## Escalation and notification 
After initial containment, move into escalation and notification mode. The objectives of this action are: 

1. Evaluate incident severity based upon impact  
    * Low – can be handled by first responders themselves. 
    * Moderate – have significant potential to affect security. Triggers IRT response and requires prompt notification to management. 
    * High – may cause critical damage to information or systems and need a full response whereby senior management are notified and the full IRT is mobilised. 
2. Escalate response to an appropriate level. 
3. Notify management and other stakeholders. 

## Containment 
The containment strategy must be evaluated on the following criteria, and balance business needs and security objectives: 

1. Damage potential. 
2. Evidence preservation. 
3. Service availability. 
4. Resource requirements. 
5. Expected effectiveness. 
6. Solution timeframe. 

Containment techniques include: 

1. Segmentation – divide networks into security zones and move affected systems into a quarantine VLAN. 
2. Isolation – move the affected system away from the rest of the network but allowing the attacker to communicate with CaC to not arouse suspicion. 
3. Removal – completely remove the affected system away from the rest of the network. 

## Eradication and recovery 
* Eradication – removes all traces of an incident. 
* Recovery – restores normal operations. 

It is good practice to rebuild any affected systems to avoid future issues. 

Endpoint security practices: 

1. Application whitelisting. 
2. Application blacklisting. 
3. Quarantine. 
4. Access controls. 

Enterprise security controls: 
1. Firewall rules. 
2. Mobile device management (MDM). 
3. Data loss prevention (DLP). 
4. URL and content filtering. 
5. Update or revoke digital certificates. 

Sanitisation and secure disposal prevent confidential information leakage. 

1. Clearing – overwrites sensitive information to frustrate casual analysis. 
2. Purging (including degaussing) – uses more advanced techniques to frustrate laboratory analysis. 
3. Destroying – completely obliterates the media through shredding, pulverization, melting, or burning. 

## Post-incident activities 
1. Lessons learned – opportunity to reflect on the incident and improve future response efforts. Lessons learned should be documented and reported. 
2. Evidence retention – consult data retention policy and any legal obligations to follow. 
3. Indicator-of-compromise generation – should be added to security monitoring program. 
4. Root cause analysis – should be included in an incident summary report. 

## Training and testing 

1. Training 
2. Tabletop – talk through of roles and responsibilities. 
3. Simulation – discuss how teams would respond in each scenario. 