cat writeup on HTB-DOG <br>
Difficulty rating **Easy** <br>
Step1: Adding Host<br>
Add dog.htb in /etc/hosts<br>
![image](https://github.com/user-attachments/assets/0fe1aebc-b523-4604-8d66-3d4ee852c17b)
<br>
run nmap scan to see open ports<br>
![image](https://github.com/user-attachments/assets/0019ac49-7abd-4d25-857f-db4c4f2e9563) <br>
by accessing the application it is found that it is based on Backdrop CMS.  
now i need to find out the version to see the availale exploits to exploit the application.  
from directory listing found user.info document and could find the version is 1.27.1.  
this specfic version is vulnerable to Authenticated RCE.  
https://www.exploit-db.com/exploits/52021?utm_source=dlvr.it&utm_medium=twitter  
now i should get minimal user access to exploit the application.  
![image](https://github.com/user-attachments/assets/e601b617-3f4c-4574-9aac-1509462bd778)
found 3 user.  
dogBackDropSystem.  
john.
tiffany@dog.htb.  
![image](https://github.com/user-attachments/assets/113c50a2-43f9-4181-a22f-918f481f689c)

need to find out the passwords of the user.  
in settings.php found mysql password
![image](https://github.com/user-attachments/assets/c7b7d3f6-4927-4df4-b7e0-ae6a3b7f503d)
tried.  
john:BackDropJ2024DS2024.  
dogBackDropSystem:BackDropJ2024DS2024.  
tiffany:BackDropJ2024DS2024.  
tiffany worked out.  




