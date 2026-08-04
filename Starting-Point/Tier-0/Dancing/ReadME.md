# Dancing

### Overview

- Platform: Windows
- Difficulty: Very Easy
- Completed: August 4, 2026

---

### Objective

Enumerate available SMB shares, access the appropriate share, and retrieve the flag.

---

### Enumeration

#### Initial Scan

```bash
nmap <target-ip>
```

Results:

```text
445/tcp open microsoft-ds
```

Performed additional enumeration:

```bash
nmap -sC -sV <target-ip>
```

Enumerated available SMB shares:

```bash
smbclient -L //<target-ip>
```

I later learned the -N option can be used to skip the password prompt entirely.

Discovered shares:

```text
ADMIN$
C$
IPC$
WorkShares
```

---

### Exploitation

Connected to the accessible SMB share.

```bash
smbclient //<target-ip>/WorkShares
```

Navigated the shared directories.

```text
ls
cd Amy.J
ls
cd James.P
ls
```

Downloaded the flag.

```text
get flag.txt
```

Exited the SMB session.

```text
exit
```

Viewed the downloaded file locally.

```bash
cat flag.txt
```

---

### Flag

Successfully retrieved the flag from the WorkShares SMB share.

---

### What I Learned

- `smbclient -L` lists available SMB shares on a target.
- Administrative shares (`ADMIN$`, `C$`, `IPC$`) are usually not the first place to investigate.
- `smbclient` uses its own command set, similar to FTP.
- Files must be downloaded with `get` before they can be viewed locally.
- Linux uses forward slashes (`//server/share`) when connecting with `smbclient`, not Windows backslashes.

---

### Tools Used

- Kali Linux
- Nmap
- smbclient

---

### Commands Used

#### Linux

```bash
nmap <target-ip>

nmap -sC -sV <target-ip>

smbclient -L <target-ip>

smbclient //<target-ip>/WorkShares

cat flag.txt.txt
```

#### SMB Client

```text
ls
cd Amy.J
cd James.P
pwd
get flag.txt
help
exit
```
