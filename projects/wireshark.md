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
- Detected repeated DNS queries to unknown domains
- TLS handshake failures indicating possible interception attempts

## Remediation
- Block suspicious domains
- Enforce TLS 1.2+
- Validate certificate chains

## Conclusion
This project demonstrates the ability to detect anomalies and analyze encrypted traffic.
