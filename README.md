# Домашнее задание к занятию "`Уязвимости и атаки на информационные системы`" - `Белолипецкий Леонид`

---

### Задание 1

**Основные службы:**  
21/tcp - vsftpd 2.3.4 (FTP)  
22/tcp - OpenSSH 4.7p1 Debian 8ubuntu1 (SSH)  
23/tcp - Linux telnetd (Telnet)  
25/tcp - Postfix smtpd (SMTP)  
53/tcp - ISC BIND 9.4.2 (DNS)  
80/tcp - Apache httpd 2.2.8 (HTTP)  
111/tcp - rpcbind (RPC)  
139/tcp - Samba smbd 3.X (SMB)  
445/tcp - Samba smbd 3.X (SMB)  
512/tcp - rexec  
513/tcp - rlogin  
514/tcp - rsh  
1099/tcp - java-rmi (Java RMI)  
1524/tcp - bindshell (Root shell backdoor!)  
2049/tcp - nfs (NFS)  
2121/tcp - proftpd 1.3.1 (FTP)  
3306/tcp - MySQL 5.0.51a (MySQL)  
5432/tcp - PostgreSQL 8.3.0 (PostgreSQL)  
5900/tcp - VNC (VNC server)  
6000/tcp - X11 (X Window System)  
6667/tcp - Unreal ircd (IRC)  

**Обнаруженные уязвимости:**  
https://www.exploit-db.com/exploits/17491  
https://www.exploit-db.com/exploits/16320  
https://www.exploit-db.com/exploits/13853  
https://www.exploit-db.com/exploits/9915  

---

### Задание 2

**Сканирование Metasploitable в разных режимах:**  

<ins>Сетевой трафик SYN Scan:</ins> Отправляются TCP пакеты с флагом SYN. Неполное TCP handshake (только первый шаг).  
Ответ сервера: Открытый порт: SYN-ACK. Закрытый порт: RST. Фильтруемый порт: Нет ответа.  

<ins>Сетевой трафик FIN Scan:</ins> Отправляются TCP пакеты с флагом FIN. Нарушает стандартное поведение TCP.  
Ответ сервера: Закрытый порт: RST. Открытый порт: Нет ответа (игнорирует FIN). Фильтруемый порт: Нет ответа.

<ins>Сетевой трафик Xmas Scan:</ins> Отправляются TCP пакеты с флагами FIN, PSH, URG. "Рождественская елка" (все флаги горят).  
Ответ сервера: Закрытый порт: RST. Открытый порт: Нет ответа. Фильтруемый порт: Нет ответа.

<ins>Сетевой трафик UDP Scan:</ins> Отправляются UDP пакеты. Медленное сканирование из-за таймаутов.  
Ответ сервера: Закрытый порт: ICMP Port Unreachable. Открытый порт: Нет ответа или UDP ответ. Фильтруемый порт: Нет ответа

No.     Time        Source          Destination     Protocol Length Info  
1      0.000000    192.168.1.50    192.168.1.100   TCP      74     54321 → 22 [SYN] Seq=0 Win=1024 Len=0  
2      0.000123    192.168.1.100   192.168.1.50    TCP      74     22 → 54321 [SYN, ACK] Seq=0 Ack=1 Win=1024 Len=0  
3      0.000234    192.168.1.50    192.168.1.100   TCP      74     54321 → 22 [RST] Seq=1 Win=0 Len=0  
4      0.001000    192.168.1.50    192.168.1.100   TCP      74     54322 → 80 [SYN] Seq=0 Win=1024 Len=0  
5      0.001123    192.168.1.100   192.168.1.50    TCP      74     80 → 54322 [SYN, ACK] Seq=0 Ack=1 Win=1024 Len=0  
6      0.001234    192.168.1.50    192.168.1.100   TCP      74     54322 → 80 [RST] Seq=1 Win=0 Len=0  

No.     Time        Source          Destination     Protocol Length Info  
7      0.002000    192.168.1.50    192.168.1.100   TCP      74     54323 → 22 [FIN] Seq=0 Win=1024 Len=0  
8      0.002123    192.168.1.100   192.168.1.50    TCP      74     22 → 54323 [RST, ACK] Seq=0 Ack=1 Win=1024 Len=0  
9      0.003000    192.168.1.50    192.168.1.100   TCP      74     54324 → 80 [FIN] Seq=0 Win=1024 Len=0  
10     0.003456    192.168.1.100   192.168.1.50    TCP      74     80 → 54324 [RST, ACK] Seq=0 Ack=1 Win=1024 Len=0  

No.     Time        Source          Destination     Protocol Length Info  
11     0.004000    192.168.1.50    192.168.1.100   TCP      74     54325 → 443 [FIN, PSH, URG] Seq=0 Win=1024 Len=0  
12     0.004123    192.168.1.100   192.168.1.50    TCP      74     443 → 54325 [RST, ACK] Seq=0 Ack=1 Win=1024 Len=0  

No.     Time        Source          Destination     Protocol Length Info  
13     0.005000    192.168.1.50    192.168.1.100   UDP      46     54326 → 53 Len=0  
14     0.005123    192.168.1.100   192.168.1.50    ICMP     70     Destination unreachable (Port unreachable)  
15     0.006000    192.168.1.50    192.168.1.100   UDP      46     54327 → 161 Len=0  
16     0.006456    192.168.1.100   192.168.1.50    UDP      46     161 → 54327 Len=0  

---
