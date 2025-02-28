# Fail2Ban: Detecting and Blocking Unauthorized Access

## Overview
This project demonstrates how to use Fail2Ban to detect and prevent brute-force attacks on a Linux system. Logs are analyzed using Splunk to monitor attack patterns.

## Steps
1. **Setup Fail2Ban**: Installed and configured Fail2Ban to monitor SSH logs.
2. **Simulated Attack**: Used Hydra to attempt brute-force login on the victim machine.
3. **Log Analysis**: Collected and analyzed logs in Splunk.
4. **Automated Blocking**: Confirmed attacker IP banning via Fail2Ban.

## Commands Used
### Fail2Ban Configuration
```bash
sudo nano /etc/fail2ban/jail.local
```

Add:
```
[sshd]
enabled = true
port = ssh
logpath = /var/log/auth.log
maxretry = 3
bantime = 600
findtime = 600
```


Brute-Force Attack Simulation
```
hydra -l admin -P passwords.txt 10.0.1.111 ssh
```

Outcomes
- Attack logs were successfully captured
- Attacker IP was automatically blocked
- Logs were visualized in Splunk

Conclusion
This project shows how Fail2Ban can effectively prevent brute-force attacks on Linux systems. Logs provide visibility into attack patterns, enhancing security monitoring.

