\# Lab 001 — CIA Triad Demonstration



\#lab #securityplus #cia #windows #commandline #blueprint



\---



\## 🎯 Objective



Demonstrate core security principles:



\* #confidentiality

\* #integrity

\* #availability



Using local Windows commands and observable outcomes.



\---



\## 🖥️ Environment



\* OS: #windows11

\* Shell: #cmd

\* Path: `C:\\lab\_cia`

\* Asset: `data.txt`



\---



\## 🧱 Step 1 — Asset Creation #asset #baseline



```bash

mkdir C:\\lab\_cia

cd C:\\lab\_cia

echo This is sensitive data > data.txt

```



\### 🔍 Verification



```bash

dir

type data.txt

```



\### 🧠 Insight



\* No asset → no need for security

\* Establishes baseline state



\---



\## 🔐 Step 2 — Confidentiality #confidentiality #accesscontrol #preventive



```bash

icacls data.txt /inheritance:r

icacls data.txt /grant %username%:F

```



\### 🔍 Verification



```bash

icacls data.txt

```



\### 🎯 Result



\* Only authorized user has access

\* Removed inherited permissions



\### 🧠 Insight



\* Access control enforces \*\*who can see data\*\*

\* Maps to #preventive control



\---



\## 🧬 Step 3 — Integrity #integrity #hashing #detective



```bash

certutil -hashfile data.txt SHA256

echo attacker was here >> data.txt

certutil -hashfile data.txt SHA256

```



\### 🎯 Result



\* Hash values changed after modification

\* Any change → detectable



\### 🧠 Insight



\* Integrity = trustworthiness of data

\* Maps to #detective control



\---



\## ⚡ Step 4 — Availability #availability #resilience #corrective



```bash

rename data.txt data.bak

type data.txt

rename data.bak data.txt

```



\### 🎯 Result



\* File inaccessible → availability failure

\* File restored → access regained



\### 🧠 Insight



\* Availability = accessible when needed

\* Maps to #corrective control



\---



\## 📊 Control Mapping #controls #pddccd



| Action             | CIA              | Control Type |

| ------------------ | ---------------- | ------------ |

| icacls permissions | #confidentiality | #preventive  |

| hash comparison    | #integrity       | #detective   |

| restore file       | #availability    | #corrective  |



\---



\## 🧠 Key Concepts #recall #exam



\* Confidentiality → who can access

\* Integrity → has it changed

\* Availability → can I access it



\---



\## 🗣️ Interview Statement #interview #portfolio



“I demonstrated the CIA triad by restricting access using icacls, validating file integrity with SHA256 hashing, and simulating availability loss and recovery through controlled file access disruption.”



\---



\## 🔗 Related Notes



\* \[\[Security Controls]]

\* \[\[CIA Triad]]

\* \[\[Hashing Concepts]]



\---



\## 🚀 Future Improvements #nextsteps



\* Add file monitoring (#detective)

\* Implement encryption (#confidentiality)

\* Automate backups (#corrective)



\---



