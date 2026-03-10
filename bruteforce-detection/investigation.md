## Investigation Overview

Alert Type: Multiple Failed VPN Login Attempts  
Investigation Type: Brute Force Detection  
Environment: Simulated SOC Lab  
Analyst: Deyse

# Investigation Process

## Step 1 — Review Authentication Logs

The SIEM alert indicated multiple failed login attempts targeting the user **j.silva**.  
The first step was to review the authentication logs around the time of the alert.

### Command Used

```bash
grep "j.silva" vpn-authentication.log

Findings:
- 27 failed login attempts
- Same source IP
- Failure reason: invalid credentials
- Attempts spaced approximately every 9 seconds

This regular timing pattern suggests automated behavior.

## Step 2 – IP Activity Pivot

The source IP was queried across authentication logs.

### Command Used

```bash
grep "185.199.110.23" vpn-authentication.log

Additional failed attempts were detected:

- m.rodrigues (3 attempts)
- a.santos (2 attempts)

All attempts followed the same pattern and failure reason.

This indicates a multi-account brute force attempt.

## Step 3 – Post-Attack Activity Review

Authentication logs were reviewed for the affected users after the attack window.

### Command Used

```bash
grep "j.silva" user-login-baseline.log

Findings:
- j.silva successfully logged in at 03:41 from internal IP 192.168.14.22
- This login aligns with the user's normal maintenance schedule
- No evidence of compromise or unusual activity