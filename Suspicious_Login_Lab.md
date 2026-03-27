\# Suspicious Login Detection Lab



\## #AAA #SecurityPlus #SOC #WindowsLogs #Detection #BlueTeam



\---



\## 🔗 Overview



Simulated and analyzed a suspicious login pattern using Windows Event Viewer to understand how authentication failures followed by a successful login may indicate potential brute-force or credential compromise activity.



\---



\## 🧠 Concepts Applied



\* #Authentication → Event ID 4624 (Successful login)

\* #Authorization → Event ID 4672 (Elevated privileges assigned)

\* #Accounting → Windows Security Logs (Event Viewer)

\* #Detection → Pattern recognition across login events



\---



\## 🧪 Lab Setup



\*\*Environment:\*\*



\* Windows 11 Host Machine

\* Event Viewer (`eventvwr`)

\* Local user account login



\---



\## ⚙️ Actions Performed



1\. Locked system (`Win + L`)

2\. Entered incorrect password multiple times

3\. Logged in successfully with correct credentials

4\. Opened Event Viewer → Windows Logs → Security

5\. Identified relevant Event IDs



\---



\## 🔍 Observed Events



| Event ID | Type          | Description                 |

| -------- | ------------- | --------------------------- |

| 4625     | Audit Failure | Failed login attempt        |

| 4624     | Audit Success | Successful login            |

| 4672     | Audit Success | Special privileges assigned |



\---



\## 🚨 Detection Pattern



```

4625 → 4625 → 4624 → 4672

```



\*\*Interpretation:\*\*



\* Multiple failed logins followed by success may indicate:



&#x20; \* Password guessing

&#x20; \* Brute-force attempt

&#x20; \* Unauthorized access with valid credentials



\---



\## ⚠️ Risk Assessment



\* Successful login after repeated failures increases likelihood of compromise

\* Presence of Event ID 4672 indicates administrative-level access

\* Potential for privilege abuse or lateral movement



\---



\## 🛠️ Response Considerations



\* Validate user identity

\* Check login timestamps for anomalies

\* Review source system / IP (if available)

\* Correlate with additional logs (process creation, network activity)



\---



\## 🧠 Key Takeaways



\* AAA is directly observable in system logs

\* Event correlation is critical for detection

\* Not all successful logins are safe

\* Context determines threat level



\---



\## 📌 Portfolio Value



This lab demonstrates:



\* Practical understanding of AAA concepts

\* Ability to analyze Windows security logs

\* Entry-level SOC analyst detection workflow

\* Real-world security thinking beyond theory



\---



