# Task 2: Secured and Monitored Web Infrastructure

## Infrastructure Components

### What are firewalls for
- Checks every visitor (network packet)
- Allows or blocks based on rules
- Protects what's inside from external threats

### Why is the traffic served over HTTPS
- Data protection
- Authentication  
- Encryption

### What monitoring is used for
- Performance tracking
- Running properly?
- Error detection
- Capacity handling
- Security alerts

### How the monitoring tool is collecting data
Agents installed on servers. Act as agents monitoring. They watch everything, report back, and create visual reports.

### Explain what to do if you want to monitor your web server QPS
Install monitor agent. Configure request counting. Create visual charts showing QPS over time. Create alert levels. Monitor patterns.

## Infrastructure Issues

### Why terminating SSL at the load balancer level is an issue
The data becomes unencrypted between the load balancer and servers, so hackers who get into the internal network can steal passwords and personal information.

### Why having only one MySQL server capable of accepting writes is an issue
If the Primary database fails, the entire website cannot save any new information or updates, making it read-only even though users can still view old data.

### Why having servers with all the same components (database, web server and application server) might be a problem
It wastes resources, makes scaling difficult since you can't add just web servers or just databases, and creates more security risks because every server has more components that can be hacked.