\# Full Attack Timeline Lab



\## #SecurityPlus #SOC #WindowsLogs #Detection #AAA #ProcessMonitoring #ThreatAnalysis



\---



\## 🔗 Overview



This lab simulates and analyzes a full authentication-to-execution sequence using Windows Security Event Logs. The goal is to correlate login activity, privilege assignment, and process execution into a single detection timeline.



\---



\## 🧠 Concepts Applied



\* #Authentication → Event ID 4624 (successful login)

\* #Authorization → Event ID 4672 (privileged access)

\* #Accounting → Event logs (Windows Security Log)

\* #Detection → Event correlation across timeline

\* #ProcessMonitoring → Event ID 4688 (process creation)



\---



\## 🧪 Lab Setup



\*\*Environment:\*\*



\* Windows 11 Host

\* Event Viewer (`eventvwr`)

\* PowerShell auditing enabled for process creation



\---



\## ⚙️ Actions Performed



1\. Locked system (`Win + L`)

2\. Entered incorrect password multiple times

3\. Logged in successfully

4\. Triggered process execution:



&#x20;  \* cmd.exe

&#x20;  \* powershell.exe

&#x20;  \* notepad.exe

5\. Opened Event Viewer → Windows Logs → Security



\---



\## 🔍 Observed Event Chain



```text

4625 → 4625 → 4624 → 4672 → 4688

```



\---



\## 🔎 Event Breakdown



\### 🔐 Authentication



\* \*\*4625\*\* → Failed login attempts

\* \*\*4624\*\* → Successful login



\*\*Insight:\*\*

Repeated failures followed by success may indicate password guessing or credential compromise.



\---



\### 🔓 Authorization



\* \*\*4672\*\* → Special privileges assigned



\*\*Insight:\*\*

User account obtained administrative-level access.



\---



\### ⚙️ Process Execution



\* \*\*4688\*\* → Process created



Examples observed:



\* powershell.exe launched by cmd.exe

\* notepad.exe launched by explorer.exe



\*\*Insight:\*\*

Post-authentication activity reveals user or attacker behavior.



\---



\## 🚨 Detection Analysis



\### Suspicious Pattern Identified



\* Multiple failed logins followed by success

\* Immediate privilege escalation

\* Execution of command-line tools



\### Risk Indicators



\* Brute-force or credential guessing attempt

\* Privileged access acquisition

\* Potential for lateral movement or system manipulation



\---



\## 🛠️ Response Considerations



\* Verify user identity and intent

\* Review login timestamps and frequency

\* Analyze process chains (parent/child relationships)

\* Correlate with network activity if available

\* Monitor for persistence mechanisms



\---



\## 🧠 Key Takeaways



\* Security events must be analyzed in sequence, not isolation

\* AAA provides identity context; process logs provide behavior context

\* Event correlation is essential for real-world detection

\* Logging visibility is critical for security operations



\---



\## 📌 Portfolio Value



This lab demonstrates:



\* Ability to correlate multiple Windows Event IDs

\* Understanding of authentication, authorization, and execution flow

\* Entry-level SOC analysis capability

\* Practical threat detection mindset using system logs



\---



