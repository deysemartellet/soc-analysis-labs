# Incident Report

## Summary

At 14:12, suspicious PowerShell activity was detected on endpoint **WS-23** associated with user **a.santos**. Investigation revealed a multi-stage attack involving encoded PowerShell execution, external communication, privilege escalation, and persistence.

---

## Timeline

- 14:11:02 — Word document opened
- 14:12:33 — Encoded PowerShell executed
- 14:14:xx — Outbound connection to external IP
- 14:17:41 — `backup_admin` user created
- 14:17:42 — User added to Administrators group
- 14:18:10 — Login using `backup_admin`
- 14:18:22 — Payload downloaded
- 14:18:45 — Payload executed
- 14:20:12 — Scheduled task created

---

## Assessment

**Confirmed endpoint compromise**

Attack stages:
- Initial access via malicious document
- Execution using encoded PowerShell
- Command & Control communication
- Privilege escalation
- Persistence via scheduled task

No confirmed data exfiltration observed.

---

## Recommended Actions

- Isolate affected host (WS-23)
- Disable `backup_admin` account
- Reset credentials for a.santos
- Block IP `45.77.112.9`
- Perform full system scan and forensic analysis
- Notify security team and affected user
- Review email filtering and macro policies

---

## Conclusion

This incident represents a successful endpoint compromise initiated through a malicious document, followed by execution, persistence, and remote control establishment.