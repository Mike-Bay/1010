# Incident Report: DNS and ICMP Traffic Log Issue Using `tcpdump`

## Summary

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
