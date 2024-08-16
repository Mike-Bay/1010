# Incident Report: DNS and ICMP Traffic Log Issue Using `tcpdump`

## Summary

<details>
<summary><h2>tcpdump log</h2></summary>
<br>
<pre>
14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A?
yummyrecipesforme.com. (24)
14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084 1/0/0 A
203.0.113.22 (40)
14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http: Flags
[S], seq 2873951608, win 65495, options [mss 65495,sackOK,TS val 3302576859
ecr 0,nop,wscale 7], length 0
14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086: Flags
[S.], seq 3984334959, ack 2873951609, win 65483, options [mss 65495,sackOK,TS
val 3302576859 ecr 3302576859,nop,wscale 7], length 0
14:18:36.786529 IP your.machine.36086 > yummyrecipesforme.com.http: Flags
[.], ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859],
length 0
14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http: Flags
[P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302576859 ecr
3302576859], length 73: HTTP: GET / HTTP/1.1
14:18:36.786595 IP yummyrecipesforme.com.http > your.machine.36086: Flags
[.], ack 74, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859],
length 0
…<a lot of traffic on the port 80>...
14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A?
greatrecipesforme.com. (24)
14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899 1/0/0 A
192.0.2.17 (40)
14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http: Flags
[S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS val 3302989649
ecr 0,nop,wscale 7], length 0
14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378: Flags
[S.], seq 1993648018, ack 1020702884, win 65483, options [mss 65495,sackOK,TS
val 3302989649 ecr 3302989649,nop,wscale 7], length 0
14:25:29.576524 IP your.machine.56378 > greatrecipesforme.com.http: Flags
[.], ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649],
length 0
14:25:29.576590 IP your.machine.56378 > greatrecipesforme.com.http: Flags
[P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302989649 ecr
3302989649], length 73: HTTP: GET / HTTP/1.1
14:25:29.576597 IP greatrecipesforme.com.http > your.machine.56378: Flags
[.], ack 74, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649],
length 0
…<a lot of traffic on the port 80>...
</pre>
</details>


- **Issue Detected**: 
  - **Protocol Involved**: UDP
  - **Problem**: Packet undeliverable to port 53 of the DNS server.
  - **Error Message**: ICMP echo reply showed "udp port 53 unreachable with length 254."
  - **Port Affected**: Port 53 (used for DNS server communications)
  - **Likely Cause**: The web server was down, possibly attacked by malicious actors.

## Analysis of the Data

### Time of Incident
- **Initial Detection**: 1:24 PM and 32 seconds.
- **Subsequent Failures**: ICMP packets were sent at 1:26 PM and 1:28 PM with the same delivery error.

### Awareness
- **Discovery**: The incident was reported by five recruitment team members who could not access the company website during closing hours. 
- **Suspected Cause**: Disgruntled former employees potentially causing the disruption.

### Actions Taken by the IT Department
- **Investigation**: 
  - The network security team used `tcpdump` to analyze network traffic.
  - Discovered that port 443 (for HTTPS) was also inaccessible.
- **Steps Taken**:
  1. **Firewall Configuration Check**: Assessed firewall settings to determine if port 53 was blocked.
  2. **System Administrator Engagement**: Contacted the web server’s administrator to check for signs of attack.
  3. **Restoring Access**: Worked to restore access to the secure web portal, including troubleshooting issues related to port 443.

## Key Findings
- **Port Affected**: Port 53 (DNS service).
- **DNS Server**: Inaccessible, likely due to an attack.
- **Additional Findings**: Port 443 (HTTPS) was also found to be inaccessible.

## Next Steps
- **Ongoing Investigation**: Continued analysis to address all potential vulnerabilities and prevent future occurrences.
- **Monitoring**: The IT department remains vigilant and continues to monitor the network for further anomalies.

**Note**: The investigation is ongoing to ensure that all potential vulnerabilities are addressed and to prevent future occurrences.
