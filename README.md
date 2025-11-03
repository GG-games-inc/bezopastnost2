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

---
