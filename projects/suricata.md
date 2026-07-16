# Network Traffic Analysis with Suricata 

## Overview
This project demonstrates practical network forensics skills using Suricata.  
The objective was to capture, analyze, and classify network traffic, identify anomalies, and validate normal encrypted communication patterns.

---

## Tools Used
- Suricata IDS (rule-based detection)
- Npcap (packet capture driver)
- Custom Suricata rules (local.rules)

---

## Findings
07/06/2026-20:31:43.619776  [**] [1:1000001:0] ICMP Ping Detected [**] [Classification: (null)] [Priority: 3] {IPv6-ICMP}
07/06/2026-20:31:54.741788  [**] [1:1000001:0] ICMP Ping Detected [**] [Classification: (null)] [Priority: 3] {ICMP}

```json
{"timestamp":"2026-07-06T20:31:43.619776-0900","event_type":"alert","proto":"IPv6-ICMP","ip_v":6,"icmp_type":135,"icmp_code":0,"pkt_src":"wire/pcap","alert":{"action":"allowed","gid":1,"signature_id":1000001,"rev":0,"signature":"ICMP Ping Detected","category":"","severity":3},"direction":"to_server","flow":{"pkts_toserver":1,"pkts_toclient":0,"bytes_toserver":86,"bytes_toclient":0,"start":"2026-07-06T20:31:43.619776-0900"}}
```


---

## Suricata Rules Used
```snort
alert icmp any any -> any any (msg:"ICMP Ping Detected"; sid:1000001;)
alert udp any any -> any 53 (msg:"Suspicious DNS Query"; content:"xyz"; sid:1000002;)
alert tcp any any -> any any (flags:S; msg:"Possible SYN Scan"; sid:1000003;)
