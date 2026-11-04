# Security Control Types (Windows)

## Objective

Implement and validate all major security control types in a Windows environment.

---

## Environment

* Host: Windows 11 (HP OmniDesk)
* Shell: Command Prompt (cmd)
* Directory: `C:\Users\Waegn\Desktop\Waegns-labs`

---

## Control Implementations

### Preventive Control

**Command**

```cmd
icacls data.txt /deny Everyone:(W)
```

**What It Does**

Prevents unauthorized modification via file permissions.

---

### Detective Control

**Command**

```cmd
certutil -hashfile data.txt SHA256
```

**What It Does**

Detects file changes through hash comparison.

---

### Corrective Control

**Command**

```cmd
copy backup_data.txt data.txt
```

**What It Does**

Restores original data after compromise.

---

### Directive Control

**Command**

```cmd
echo DO NOT MODIFY THIS FILE > policy.txt
```

**What It Does**

Defines expected user behavior.

---

### Deterrent Control

**Command**

```cmd
echo Unauthorized access will be logged >> policy.txt
```

**What It Does**

Discourages unauthorized actions via warning.

---

### Compensating Control

**Command**

```cmd
copy data.txt backup_data.txt
```

**What It Does**

Provides alternative protection when primary controls fail.

---

## Key Takeaways

* Security is layered (defense in depth)
* Humans are part of the attack surface (human factor)
* Detection without response is useless (incident response)
* Backups are recovery, not prevention (resilience)

---

## Mapping Summary

| Control Type | Implementation     |
| ------------ | ------------------ |
| Preventive   | icacls permissions |
| Detective    | hashing (certutil) |
| Corrective   | restore file       |
| Directive    | policy file        |
| Deterrent    | warning message    |
| Compensating | backup file        |

---

## Next Step

AAA (Authentication, Authorization, Accounting): see [Suspicious Login Detection](../detection/suspicious-login-detection.md).
