Incident Summary

At 02:47 AM, multiple failed VPN login attempts were detected targeting user accounts j.silva (27 attempts), m.rodrigues (3 attempts), and a.santos (2 attempts) within a 4-minute window.

Log analysis confirmed all attempts originated from a single external IP address (185.199.110.23), with consistent ~9-second intervals and identical failure reasons (invalid credentials), indicating automated brute force behavior.

No successful authentication occurred, no account lockouts were triggered, and no evidence of lateral movement or data exfiltration was observed.

Assessment: Confirmed automated brute force attempt with no signs of account compromise.

Recommended Actions: Block the source IP, notify affected users, enforce password reset, and ensure MFA is enabled to mitigate future credential-based attacks.