\# 🧪 Lab: Security Control Types (Windows) #lab #security #secplus #windows #defense-in-depth



\## 🎯 Objective



Implement and validate all major security control types in a Windows environment.



\#objective #security-controls #hands-on



\---



\## 🧱 Environment



\* Host: Windows 11 (HP OmniDesk)

\* Shell: Command Prompt (cmd)

\* Directory: `C:\\Users\\Waegn\\Desktop\\Waegns-labs`



\#environment #windows #cmd #homelab



\---



\## ⚙️ Control Implementations



\### 🛡️ Preventive Control #preventive #technical-control



\*\*Command\*\*



```cmd

icacls data.txt /deny Everyone:(W)

```



\*\*What It Does\*\*

Prevents unauthorized modification via file permissions.



\---



\### 🔍 Detective Control #detective #integrity #hashing



\*\*Command\*\*



```cmd

certutil -hashfile data.txt SHA256

```



\*\*What It Does\*\*

Detects file changes through hash comparison.



\---



\### 🔧 Corrective Control #corrective #recovery



\*\*Command\*\*



```cmd

copy backup\_data.txt data.txt

```



\*\*What It Does\*\*

Restores original data after compromise.



\---



\### 📜 Directive Control #directive #policy #administrative-control



\*\*Command\*\*



```cmd

echo DO NOT MODIFY THIS FILE > policy.txt

```



\*\*What It Does\*\*

Defines expected user behavior.



\---



\### 🚫 Deterrent Control #deterrent #awareness #behavior



\*\*Command\*\*



```cmd

echo Unauthorized access will be logged >> policy.txt

```



\*\*What It Does\*\*

Discourages unauthorized actions via warning.



\---



\### ♻️ Compensating Control #compensating #fallback #resilience



\*\*Command\*\*



```cmd

copy data.txt backup\_data.txt

```



\*\*What It Does\*\*

Provides alternative protection when primary controls fail.



\---



\## 🧠 Key Takeaways #lessons-learned #secplus



\* Security is layered (#defense-in-depth)

\* Humans are part of the attack surface (#human-factor)

\* Detection without response is useless (#incident-response)

\* Backups are recovery, not prevention (#resilience)



\---



\## 📌 Mapping Summary #cheatsheet



| Control Type | Implementation     |

| ------------ | ------------------ |

| Preventive   | icacls permissions |

| Detective    | hashing (certutil) |

| Corrective   | restore file       |

| Directive    | policy file        |

| Deterrent    | warning message    |

| Compensating | backup file        |



\---



\## 🪖 Operator Notes #portfolio #interview-ready



\* Demonstrated layered security controls in Windows

\* Simulated real-world integrity + recovery workflow

\* Bridges technical + administrative security concepts



\---



\## 🚀 Next Step #next-steps #aaa



➡️ AAA (Authentication, Authorization, Accounting)



