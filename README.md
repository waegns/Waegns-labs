# Waegns Labs

Hands-on IT and cybersecurity labs: Windows security controls, log-based threat detection, and offensive security in an isolated lab. Each write-up covers the objective, exact commands, evidence, and what I learned.

## Lab Index

| Lab | Area | What it shows | Tools |
| --- | --- | --- | --- |
| [Full Attack Timeline](detection/full-attack-timeline.md) | Detection | Correlated failed logins, successful login, privilege assignment, and process execution into one timeline | Event Viewer, Event IDs 4624 / 4625 / 4672 / 4688 |
| [Suspicious Login Detection](detection/suspicious-login-detection.md) | Detection | Simulated repeated failed logins followed by success; mapped events to Authentication, Authorization, and Accounting (AAA) | Event Viewer, Event IDs 4624 / 4625 / 4672 |
| [Process Creation Monitoring](detection/process-creation-monitoring.md) | Detection | Enabled process auditing and analyzed parent/child process chains for suspicious patterns | Audit policy, Event ID 4688 |
| [Security Control Types](windows-security/security-control-types.md) | Windows security | Implemented all six control types; baseline → tamper → detect → restore → verify | icacls, certutil (SHA256), cmd |
| [CIA Triad Demonstration](windows-security/cia-triad.md) | Windows security | Demonstrated confidentiality, integrity, and availability with built-in Windows tools | icacls, certutil, cmd |
| [vsFTPd 2.3.4 Backdoor](offensive/vsftpd-backdoor-exploit.md) | Offensive security | Enumerated and exploited a known backdoor on Metasploitable2 in an isolated network | Nmap, Metasploit, Kali Linux |

## Repository Structure

```text
detection/          Windows Security Event Log analysis and threat detection
windows-security/   Security controls and CIA triad on Windows 11
offensive/          Exploitation labs against intentionally vulnerable targets
```

## Lab Environment

- Windows 11 host for the detection and Windows security labs
- Kali Linux and Metasploitable2 virtual machines on an isolated internal network (192.168.56.0/24)
- All offensive work is performed only against lab systems I own

## Related Projects

- [windows-ui-freeze-troubleshooting](https://github.com/waegns/windows-ui-freeze-troubleshooting): root-cause analysis of a Windows 11 Explorer freeze caused by an unstable network share
- [scribe](https://github.com/waegns/scribe): Python + local LLM tool that turns raw lab output into sanitized documentation

## Skills Demonstrated

Security monitoring · Windows event log analysis · Threat detection · Access control · File integrity verification · Service enumeration · Exploitation · Root cause analysis · Technical documentation · Git
