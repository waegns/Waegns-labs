\# Process Creation Monitoring Lab



\## #SecurityPlus #WindowsLogs #Detection #SOC #ProcessMonitoring



\---



\## 🔗 Overview



Monitored process execution using Windows Event ID 4688 to understand how systems log program activity and how this data can be used for threat detection.



\---



\## 🧠 Concept



Event ID 4688 logs when a new process is created, including:

\- Process name

\- Parent process

\- User account



\---



\## 🧪 Actions Performed



\- Enabled process creation auditing

\- Executed programs:

&#x20; - notepad.exe

&#x20; - calc.exe

&#x20; - cmd.exe

&#x20; - powershell.exe

\- Reviewed logs in Event Viewer



\---



\## 🔍 Observed Events



Event ID: 4688



Examples:

\- notepad.exe launched by explorer.exe

\- powershell.exe launched by cmd.exe



\---



\## 🚨 Detection Insight



Suspicious patterns include:

\- PowerShell launched from unusual parent processes

\- Command shells spawning other shells

\- Unknown executables



\---



\## 🛠️ Response Considerations



\- Verify user intent

\- Check frequency and timing

\- Correlate with login events (4624)

\- Investigate process chains



\---



\## 🧠 Key Takeaways



\- Event 4688 provides visibility into system activity

\- Process chains are critical for detection

\- Logging must be enabled for visibility

\- Context determines whether activity is malicious

