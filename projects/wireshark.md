# Network Traffic Analysis with Wireshark

## Objective
Analyze network traffic to identify suspicious DNS and TLS behavior.

## Tools
Wireshark

## Procedure
- Captured traffic from a test environment
- Filtered DNS and TLS packets
- Identified anomalies in handshake patterns

## Findings
- **Repeated DNS queries to a discontinued third‑party service were observed.**
  - The client attempted multiple record types (A, AAAA, HTTPS, IPv6), generating unnecessary DNS noise caused by a webpage still referencing outdated scripts.

- **Normal TCP behavior**, including clean session termination, new TCP handshakes to DNS servers, benign retransmissions, and small PSH/ACK packets consistent with DNS over TCP.

- **Normal ARP resolution** between gateway and host, with no evidence of ARP spoofing or poisoning.

## Remediation
- Review and update webpages or applications referencing deprecated external scripts to reduce unnecessary DNS traffic.
- Monitor DNS logs for recurring queries to discontinued or unreachable domains.
- No further action required, as TCP and ARP behavior is normal and shows no indicators of compromise.

## Conclusion
This project demonstrates the ability to identify benign anomalies, distinguish normal encrypted traffic patterns, and validate network behavior using Wireshark.

