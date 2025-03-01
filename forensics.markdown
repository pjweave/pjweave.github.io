---
layout: page
title: Digital forensics
permalink: /forensics/
---
![Disk platter][irhimg]

Investigative techniques to collect, preserve, analyse, and interpret digital evidence. 

[irhimg]: /images/digital-forensics.jpg "Disk platter"

## #1 principle
Investigations must <b>never alter evidence</b>. Create copies (or images) of the original physical evidence and analyse the image during analysis. Never try to perform forensics yourself unless you’ve received appropriate training. 

Write blockers (a.k.a. forensic disk controllers) prevent accidental modification of disks during imaging. 

Hashes protect evidence by providing a unique file signature that indicates whether a file has changed over time. Digital signatures provide non-repudiation. 

File metadata contains a wealth of information. 

## Volatility
Relative permanence of evidence; short-lived evidence is more volatile than long-lived evidence. 

Order of volatility (most to least volatile): 

1. Network traffic. 
2. Memory contents. 
3. System and process data. 
4. Files (swap space first). 
5. Logs 
6. Archived records. 

Time offsets: help correlate records from different sources. 

Consider alternate evidence sources, e.g. witness statements, video surveillance/recordings, screenshots, memory contents, process table, O/S configuration. 

## Chain of custody
Provides a paper trail of evidence. Evidence should be labelled and stored in a sealed evidence container. Each piece of evidence should be accompanied by an evidence log that should include the following. They must be available to present in court: 

1. Initial collection.  
2. Transfer. 
3. Storage. 
4. Opening and resealing the container. 
5. Name of investigator, date and time, purpose, and nature of the action. 

## E-discovery
A legal hold that requires the preservation of relevant electronic and paper records. 

1. Collection and preservation: ensure evidence is not tampered with and establish a provenance. System administrators must suspend the automatic deletion of relevant logs. Security teams and electronic discovery management systems often assist in collection efforts. 
2. Production: present documents to the other side. Most litigation holds never move forward to the production phase. 

Sources of electronic records: 

1. File servers. 
2. Endpoint systems. 
3. Email messages. 
4. Enterprise systems and cloud services. 
5. Firewall logs. 
6. Application logs. 
7. Endpoint logs. 
8. OS-specific security logs. 
9. IDS/IPS logs. 
10. Network logs. 

Other sources: 

1. Metadata. 
2. Vulnerability scans. 
3. Automated reports. 
4. Dashboards. 
5. Packet captures. 
