# Web Application Fuzzing with Wfuzz

## Objective
Discover hidden endpoints and test input validation.

## Tools
Wfuzz

## Procedure
- Enumerated directories using wordlists
- Tested parameters for improper validation
- Logged responses and anomalies

## Findings
- Hidden `/admin/test` endpoint discovered
- Parameter `id` vulnerable to unexpected input

## Remediation
- Restrict endpoint access
- Implement server-side validation

## Conclusion
Shows capability in web fuzzing and vulnerability identification.
