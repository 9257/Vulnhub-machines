# Vulnhub-machines
Today i am going to share my first writeup for vulnhub machine "GEISHA". it was an easy box based on Linux OS.
the target is to get the root shell and then obtain the flag under/root

So Lets Jump in it ,Have Fun

first step i used nmap to find my target

![1](https://user-images.githubusercontent.com/33134699/85993651-ef884500-b9f6-11ea-8a13-51ed20d0c3a0.PNG)

found our Targets IP Address 192.168.239.144


my next step is to make scanning my target to know the open ports and services running in the this system using nmap 


![2](https://user-images.githubusercontent.com/33134699/85993290-640eb400-b9f6-11ea-85f1-9ff37ce3cbf7.PNG)

We found that target has many ports are open like 21/ftp, 22/ssh, 80/http
I explored the domain on this target IP address from port 80 http service and here we see a image file.

![3](https://user-images.githubusercontent.com/33134699/85994562-42aec780-b9f8-11ea-8bb0-094ab2beb68a.PNG)

then i scanned this domain when i get to port 7125 using nikto , i found this

![4](https://user-images.githubusercontent.com/33134699/85994873-e77fd380-b9fd-11ea-884e-49adeb3075dc.PNG)


I hit that with the browser and i found this file 

![5](https://user-images.githubusercontent.com/33134699/85994900-ffefee00-b9fd-11ea-9777-8a1137837a67.PNG)


now i have a user Geisha i decided to bruteforce the port 22/ssh using ncrack network authentication password cracking tool

![6](https://user-images.githubusercontent.com/33134699/85994948-1138fa80-b9fe-11ea-8902-0857144ce457.PNG)


i discovered geisha user credentials, now we have geisha user ssh password letmein
then i used it to logged in by the port 22/ssh

let's start Privilege Escalation 

after login i checked for SUID binaries 

![7](https://user-images.githubusercontent.com/33134699/85995003-231a9d80-b9fe-11ea-9052-d8a0f4a614a2.PNG)


now i got /usr/bin/base32 file which is having suid permissions. 

 
i got the private ssh key for the root


![8](https://user-images.githubusercontent.com/33134699/85995786-72ae9880-ba01-11ea-9478-d258532323cc.PNG)


Here i successfully retrieve the ssh key now save this key in your system
i have got root's ssh private key. now using this private ssh key we will privilege escalation for the geisha user to the root

![9](https://user-images.githubusercontent.com/33134699/85995721-61658c00-ba01-11ea-988c-2b8d626e28ae.PNG)



Here we got the root flag


That was easy machine :D


HAPPY HACKING :)
