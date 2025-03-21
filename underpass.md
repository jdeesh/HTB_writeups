writeup on HTB-Underpass <br>
Difficulty rating **Easy** <br>
Step1: Adding Host<br>
Add underpass.htb in /etc/hosts
![image](https://github.com/user-attachments/assets/be9b5900-7ae5-451b-ae42-d71fab5efbf9)

run nmap scan:
TCP Scan: nmap -v -p- -sS -T4 underpass.htb<br>
![image](https://github.com/user-attachments/assets/6f650e7e-cdee-4169-be7b-d0d3f1075b33)
UDP Scan: nmap -v -sU -p- --min-rate=1000 --max-retries 1 --disable-arp-ping underpass.htb
![image](https://github.com/user-attachments/assets/064cf41b-5d4b-4a4c-ba53-4b9a7efc5d05)

found below ports are open<br>
PORT      STATE    SERVICE<br>
22/tcp    open     ssh<br>
80/tcp    open     http<br>
161/udp   open     snmp<br>


