writeup on HTB-Underpass <br>
Difficulty rating **Easy** <br>
Step1: Adding Host<br>
Add underpass.htb in /etc/hosts
![image](https://github.com/user-attachments/assets/be9b5900-7ae5-451b-ae42-d71fab5efbf9)

run nmap scan:<br>
TCP Scan: nmap -v -p- -sS -T4 underpass.htb<br>
![image](https://github.com/user-attachments/assets/6f650e7e-cdee-4169-be7b-d0d3f1075b33)<br>
UDP Scan: nmap -v -sU -p- --min-rate=1000 --max-retries 1 --disable-arp-ping underpass.htb<br>
![image](https://github.com/user-attachments/assets/064cf41b-5d4b-4a4c-ba53-4b9a7efc5d05)
<br>
found below ports are open<br>
PORT      STATE    SERVICE<br>
22/tcp    open     ssh<br>
80/tcp    open     http<br>
161/udp   open     snmp<br>

by accessing port 80<br>
![image](https://github.com/user-attachments/assets/311d6b04-fe53-4158-b307-222fd95ee60d)<br>

lets run gobuster<br>
found /daloradius folder in gobuster<br>
![image](https://github.com/user-attachments/assets/8c9d6517-329d-418a-a3bc-d336b879731d)
<br>
by searching online, i found the link for login page and found default login username and password
![image](https://github.com/user-attachments/assets/59ea7424-1abe-4216-b90c-1e6da7f2f486)
<br>
![image](https://github.com/user-attachments/assets/d9f42ab3-030e-43cc-b4eb-788d2b2b5e07)
<br>
login with username is administrator and password is radius. <br>
![image](https://github.com/user-attachments/assets/ef5be6a8-bb0c-4365-b947-d14a458d5d31)







