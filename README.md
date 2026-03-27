# Waegns Labs

## 🔗 Overview

This repository serves as a central hub for hands-on IT and cybersecurity labs focused on real-world troubleshooting, system interaction, and security analysis.

---

## 📁 Repository Structure

* 01_Windows_Labs/ → Windows-based labs and system analysis
* Exploitation/ → Offensive security labs (Metasploit, vulnerability exploitation)
* screenshots/ → Supporting visuals

---

## 🧪 Featured Labs

### 🛡️ Suspicious Login Detection (AAA Lab)

* 🔗 https://github.com/waegns/Waegns-labs/blob/main/Suspicious_Login_Lab.md
* Simulated repeated failed login attempts followed by successful authentication
* Correlated Windows Security Event IDs:

  * 4625 (failed login)
  * 4624 (successful login)
  * 4672 (privileged access)
* Applied AAA concepts (Authentication, Authorization, Accounting) to real system logs
* Performed detection analysis and basic threat assessment

---

### 🔐 Security Control Types Lab

* 🔗 https://github.com/waegns/Waegns-labs/blob/main/Security_Control_Types.md
* Implemented all six security control types in a Windows environment:

  * Preventive (file permissions)
  * Detective (SHA256 hashing)
  * Corrective (file restoration)
  * Directive (policy enforcement)
  * Deterrent (warning messaging)
  * Compensating (backup strategy)
* Demonstrated full integrity lifecycle: baseline → tamper → detect → restore → verify

---

### 🔐 CIA Triad Demonstration

* 🔗 https://github.com/waegns/Waegns-labs/blob/main/01_Windows_Labs/Lab_CIA_Triad.md
* Demonstrated confidentiality, integrity, and availability using Windows command-line tools
* Tools: icacls, certutil, CMD

---

### 🖥️ Windows UI Freeze Troubleshooting

* 🔗 https://github.com/waegns/windows-ui-freeze-troubleshooting
* Diagnosed intermittent UI failure caused by explorer.exe and network share conflicts
* Applied structured troubleshooting methodology (observe → isolate → test → verify)

---

### ⚔️ VSFTPD Exploitation Lab

* 🔗 https://github.com/waegns/Waegns-labs/blob/main/Exploitation/vsftpd-exploit.md
* Exploited vsFTPd 2.3.4 backdoor on Metasploitable2
* Tools: Nmap, Metasploit, Netcat

---

## 🧠 Skills Demonstrated

* #SecurityMonitoring
* #LogAnalysis
* #ThreatDetection
* #WindowsEventLogs
* #AAA
* #NetworkDiagnostics
* #Linux
* #OffensiveSecurity
* #Git
* #Troubleshooting
* #RootCauseAnalysis

---

## 🎯 Objective

Develop operational capability for:

* IT Support
* Infrastructure / Data Center Operations
* Security Operations (SOC)

---

## 📈 Status

Active — continuously expanding lab portfolio with hands-on detection, troubleshooting, and system analysis exercises.
