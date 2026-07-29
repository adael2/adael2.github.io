# Burp Suite Web CTF

## Objective
Perform web application analysis using Burp Suite to identify hidden endpoints, 
detect anomalies, and gain access to restricted areas of the site.

## Tools
Burp Suite Community  
Proxy listener  
Repeater

## Procedure

### 1. Configure Burp Suite and Browser Proxy
- Set Burp Suite proxy listener.

### 2. Capture and Inspect HTTP Traffic
- Navigate through the target application while intercept is ON.
- Analyze requests and responses: headers, cookies, parameters, and server behavior.
- Identify potential attack surfaces such as query parameters, hidden fields, and API calls.

### 3. Enumerate Hidden Endpoints
- Use Proxy → HTTP History to detect patterns in URLs.
- Identify potential access by modifying the session cookie.
- Send suspicious requests to Repeater for manual testing.

### 4. Parameter Manipulation with Repeater
- Modify the session cookie to escalate privileges and obtain admin access.

### 5. Admin Access
- With the modified cookie, access restricted routes and administrative pages.

### 6. Flag Found
- The challenge flag was obtained using the admin‑level session cookie.

## Findings
- Burp Suite allowed discovery of hidden endpoints not visible in the UI.
- Session cookies could be manipulated to test authentication robustness.
- Response comparison helped identify subtle behavioral differences.

## Conclusion
This lab demonstrates practical skills in web application security testing using Burp Suite, 
including proxy interception, endpoint enumeration, session manipulation, and response analysis. 
It reflects understanding of core concepts used in pentesting, bug bounty, and SOC analysis.
