  # Man-in-the-middle (MITM) Attack Simulation Using Ettercap:
  
The purpose of this project was to simulate a man-in-the-middle attack using the Ettercap tool; in order to demonstrate packet sniffing and show the consequences of using protocols that allow for unencrypted communication such as http.
Tools Used:
1.	Kali Linux.
2.	Windows 10 VM.
3.	Ettercap.
To execute this attack, I checked the IP and MAC addresses of the Kali Linux VM, the Windows 10 VM, as well as the router.

### Kali Linux IP and MAC address info:
 
<img width="975" height="718" alt="image" src="https://github.com/user-attachments/assets/07a2c0f8-83be-459c-9a47-413e7bcec850" />


### Windows 10 IP and MAC address info:

<img width="975" height="503" alt="image" src="https://github.com/user-attachments/assets/1efeb343-2d3b-4876-b3f7-6339717f6776" />


### Windows 10 ARP Cache Before ARP Spoofing:

<img width="975" height="514" alt="image" src="https://github.com/user-attachments/assets/0c906955-d684-45ca-93f7-ba164e9bcd0d" />

 

### Ettercap Setup:
-In Ettercap, I scanned for hosts and selected the router and Windows 10 VM as the targets, then initiated ARP poisoning.
 
<img width="850" height="542" alt="image" src="https://github.com/user-attachments/assets/f5512ff8-d4f0-4edb-8745-b06d888580f7" />


-I checked the ARP cache on the Windows 10 VM both before and after initiating ARP poisoning, to confirm that the attack was successful.


### Windows 10 ARP Cache After ARP Spoofing:

<img width="975" height="479" alt="image" src="https://github.com/user-attachments/assets/e160a6d0-1c5b-4891-bb52-5646f5ca3e17" />

 
### HTTP Login Page:
-I entered the username and password on the http test login page.

<img width="948" height="502" alt="image" src="https://github.com/user-attachments/assets/f1fa11ec-ea22-446f-b691-53de67389ad0" />

 
### Wireshark Packet Capture:
-In Wireshark, the POST request with the plain-text credentials was captured.

<img width="946" height="578" alt="image" src="https://github.com/user-attachments/assets/be08a747-7142-4abf-8671-e987a0713766" />

 
## Recommendations:
1. Using HTTPS:
-Using HTTPS encrypts the traffic, so that even if it gets intercepted, the attacker/s won’t be able to interpret the data.
Illustrations:

### When using http:
User (Victim)     http request (Plain text)        Attacker     Forwarded http request   Router    


                                         Attacker sees captured packets in plain text.
                




### When using https:   
    User (Victim)    https request (Encrypted)       Attacker     Forwarded https request   Router    


                                         Attacker sees captured packets, but the data is encrypted.

2. Using a VPN: 
-When using a VPN, the traffic is sent through an encrypted tunnel between the user's device and the VPN server.
Illustrations:
### When using http without VNP:
User (Victim)     http request (Plain text)       Attacker     Forwarded http request   Router    


                                         Attacker sees captured packets in plain text.


### When using a VPN:
User (Victim)     Encrypted VPN traffic        Attacker    Encrypted VPN traffic      Router    

	
       Attacker does not see plain text data, even when using http.


                                                                                                                                       VPN Server 
                                                                                                                                       
                                                                                                                                       
-It’s best to use https even when using a VPN, because the VPN server decrypts the tunnel and if attackers gain unauthorized access to the server, the data can be seen in plain text.                       
