# CIA Triad Demonstration

## Objective

Demonstrate core security principles:

* Confidentiality
* Integrity
* Availability

Using local Windows commands and observable outcomes.

---

## Environment

* OS: Windows 11
* Shell: Command Prompt (cmd)
* Path: `C:\lab_cia`
* Asset: `data.txt`

---

## Step 1 — Asset Creation

```cmd
mkdir C:\lab_cia
cd C:\lab_cia
echo This is sensitive data > data.txt
```

### Verification

```cmd
dir
type data.txt
```

### Insight

* No asset → no need for security
* Establishes baseline state

---

## Step 2 — Confidentiality

```cmd
icacls data.txt /inheritance:r
icacls data.txt /grant %username%:F
```

### Verification

```cmd
icacls data.txt
```

### Result

* Only authorized user has access
* Removed inherited permissions

### Insight

* Access control enforces **who can see data**
* Maps to preventive control

---

## Step 3 — Integrity

```cmd
certutil -hashfile data.txt SHA256
echo attacker was here >> data.txt
certutil -hashfile data.txt SHA256
```

### Result

* Hash values changed after modification
* Any change → detectable

### Insight

* Integrity = trustworthiness of data
* Maps to detective control

---

## Step 4 — Availability

```cmd
rename data.txt data.bak
type data.txt
rename data.bak data.txt
```

### Result

* File inaccessible → availability failure
* File restored → access regained

### Insight

* Availability = accessible when needed
* Maps to corrective control

---

## Control Mapping

| Action             | CIA              | Control Type |
| ------------------ | ---------------- | ------------ |
| icacls permissions | Confidentiality  | Preventive   |
| hash comparison    | Integrity        | Detective    |
| restore file       | Availability     | Corrective   |

---

## Key Concepts

* Confidentiality → who can access
* Integrity → has it changed
* Availability → can I access it

---

## Future Improvements

* Add file monitoring (detective)
* Implement encryption (confidentiality)
* Automate backups (corrective)
