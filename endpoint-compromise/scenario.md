# Scenario

## Initial Alerts

### Alert 1 — Suspicious PowerShell Execution
- **Host:** WS-23
- **User:** a.santos
- **Time:** 14:12:33
- **Command:** powershell.exe -enc SQBFAFgAIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIABOAGUAdwAtAE8AYgBqAGUAYwB0ACkA

---

### Alert 2 — Outbound Connection
- **Host:** WS-23
- **Time:** ~14:14
- **Destination IP:** 45.77.112.9
- **Port:** 443
- **Process:** powershell.exe

---

### Alert 3 — Privilege Escalation
- **Host:** WS-23
- **Time:** 14:17:41
- **Event:** New local user created
- **User:** backup_admin

- **14:17:42**
- User added to **Administrators group**

---

## Initial Context

- Endpoint: Employee workstation
- No prior alerts on this host
- Activity occurred during business hours