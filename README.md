# Detection-of-SMB-brute-force-and-privilege-escalation-on-Active-Directory-with-Wazuh
Security monitoring lab designed to detect SMB brute-force attacks and privilege escalation within an Active Directory environment using Wazuh SIEM. Windows security logs are collected, centralized, and analyzed to identify failed authentication attempts, suspicious account creation, and administrative privilege changes.

## Disclaimer
This project was conducted strictly in a controlled lab environment for educational purposes only.

## Lab Environment
- Attacker Machine: Kali Linux
- Target Machine: Domain Controller (Window Server 2019)
- Tool: Nmap, NetExec, SMBClient, Wazuh
- Network Type: Isolated / Host-only Network
  
## Analysis flow
<b>1. Wazuh Agent</b>
<br>
Wazuh SIEM dashboard showing two active agents (Windows client and Domain Controller) successfully connected to the server, enabling centralized log collection and security monitoring within an Active Directory environment.

<b>2. SMB Brute Force</b>
<br>
SMB brute-force attack simulation using NetExec from Kali Linux against an Active Directory Domain Controller. Multiple authentication attempts are performed with a user and password list until valid credentials are discovered, demonstrating how brute-force attacks target SMB services.

<b>3. SMB Brute-force Detection</b>
<br>
Wazuh SIEM detecting multiple Windows audit failure events generated during an SMB brute-force attack against an Active Directory Domain Controller, showing how SIEM correlates failed authentication attempts into security alerts.

<b>4. Shell Access</b>
<br>
Remote command execution on the Domain Controller using Impacket PsExec, which uploads a service through Windows Admin Shares and spawns a remote shell with NT AUTHORITY\SYSTEM privileges, demonstrating lateral movement and privilege escalation in an Active Directory environment.

<b>5. Remote execution detection</b>
<br>
Wazuh SIEM detecting suspicious remote service creation on a Domain Controller, mapped to MITRE ATT&CK techniques T1021.002 (SMB/Windows Admin Shares) and T1569.002 (Service Execution), indicating potential lateral movement and remote command execution.

<b>6. Persistance and privilege escalation</b>
<br>
Privilege escalation and persistence activity where new user accounts are created and added to the Domain Admins group using Windows commands, demonstrating how attackers maintain access and gain administrative control in an Active Directory environment.

<b>7. Persistance and privilege escalation detection</b>
<br>
Wazuh SIEM detecting suspicious account creation and modification events mapped to MITRE ATT&CK T1098 (Account Manipulation), indicating potential persistence techniques where attackers create or modify user accounts to maintain access in an Active Directory environment.

<b>8. Attacker1 &  Attacker2 privilege escalation</b>
<br>
Detailed Windows Security Event logs showing user account modifications where newly created accounts (attackers1 and attackers2) were changed in the Active Directory domain, supporting Wazuh alerts for account manipulation and persistence activities.
