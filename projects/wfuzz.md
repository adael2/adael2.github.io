# Web Application Fuzzing with Wfuzz

## Objective
Discover hidden endpoints and test input validation to identify potential security weaknesses.

## Tools
Wfuzz

## Procedure
- Enumerated directories using multiple wordlists.
- Tested parameters to detect improper input validation.
- Logged anomalies, unexpected responses, and unusual status codes.

## Findings
Hidden endpoints discovered:
- `/admin/`
- `/import`
- `beta`
- `qa`
- `staging`

These endpoints responded with distinctive status codes or content patterns, indicating accessible but undocumented resources.

## Remediation
- Notify IT/security teams about exposed endpoints.
- Restrict access to non‑public environments (beta, QA, staging).
- Implement proper authentication and authorization controls.
- Validate and sanitize all input parameters server‑side.

## Conclusion
This project demonstrates proficiency in web fuzzing, endpoint discovery, and early‑stage vulnerability identification using Wfuzz.
