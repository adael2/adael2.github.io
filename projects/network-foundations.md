# Network Foundations

## Objective
Analyze available ports from a website.

## Tools
Nmap

## Procedure
```
nmap -p21,80 -sC -sV <target ip>
```
- If a port is open
```
nc <target ip> 21
```
for HTTP we use curl or wget.
- Enter Credentials
```
USER anonymous[Cntrl+V][Enter][Enter]
PASS anything[Cntrl+V][Enter][Enter]
PASV[Cntrl+V][Enter][Enter]
// Added after create a channel
LIST[Ctrl+V][Enter][Enter]
PASV[Ctrl + V][Enter][Enter]
// After creating a new channel
RETR Note-From-IT.txt[Ctrl+V][Enter][Enter]
```
- Create a channel via the last 2 numbers in the above output. Then the real port is calculated as 'p1*256 + p2'.
```
nc -v <target ip> <dynamic port>
```
- Create a new channel as before.
- For HTTP
```
nc -v <target ip> 80
```
```
GET / HTTP/1.1[enter]
Host: <target ip>[enter]
User-Agent: Server Administrator[enter][enter] // Depends on request headers
```

## Findings
- Review open port allows you to identify which ports are weak and have a plan to secure them.

## Conclusion
Shows ability to analyze available ports and document findings.
