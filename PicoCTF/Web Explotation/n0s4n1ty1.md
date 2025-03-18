# Description 

A developer has added profile picture upload functionality to a website. However, the implementation is flawed, and it presents an opportunity for you. Your mission, should you choose to accept it, is to navigate to the provided web page and locate the file upload area. Your ultimate goal is to find the hidden flag located in the /root directory.
You can access the web application `here`!

# Hints

File upload was not sanitized

Whenever you get a shell on a remote machine, check `sudo -l`

# Solution 

First, you need to learn how to scan a website using Gobuster. You can download it [here](https://github.com/OJ/gobuster/releases) for Windows or install it on Linux using:
```
sudo apt install gobuster -y
```

To start scanning, use the following command:
```
gobuster dir -u http://standard-pizzas.picoctf.net:(port)/ -w /conmmon.txt
```
With [common.txt](](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/common.txt)) is a list of common directories and files.

After running the scan, you may see output like this:
```
/.hta                 (Status: 403) [Size: 295]
/.htpasswd            (Status: 403) [Size: 295]
/.htaccess            (Status: 403) [Size: 295]
/index.php            (Status: 200) [Size: 1908]
/server-status        (Status: 403) [Size: 295]
/uploads              (Status: 301) [Size: 353] [--> http://standard-pizzas.picoctf.net:(port)/uploads/]
```

Pay attention to /uploads and /index.php. Try accessing `http://standard-pizzas.picoctf.net:(port)/index.php`, but nothing seems to happen.

You can't directly access /uploads, but consider how files uploaded to the website might be stored there. Test this by uploading an image named abc.png. If the website tells you:

`The file abc.png has been uploaded Path: uploads/abc.png`

Then, visit http://standard-pizzas.picoctf.net:(port)/uploads/abc.png to see if the file was successfully uploaded.

If the website allows you to upload a .php file, it may execute as a script. You can test this by creating a PHP file with the following content:
```
PNG
<?php
phpinfo();
?>
```
Many websites validate file uploads by checking both the file extension (.png) and the magic bytes at the beginning of the file. The magic bytes for a PNG file are:`89 50 4E 47 0D 0A 1A 0A`. Use [CyberChef](https://gchq.github.io/CyberChef/) to decode it and then you get *PNG**. Insert them at the beginning of your file, save it as run.png.php.

Now, upload run.png.php to the website. If successful, access `/uploads/run.png.php`. If PHP is enabled, you should see the phpinfo() page.
You may not know this: If you upload a valid PHP web shell file, it can run directly on that website, allowing you to execute commands remotely on the server!

To get a working shell, use a simple PHP web shell lik [this](https://gist.github.com/joswr1ght/22f40787de19d80d110b37fb79ac3985), Modify the script by adding PNG magic bytes and rename it to shell.png.php.

Upload it and access /uploads/shell.png.php. If successful, you will get a web shell.

Execute the command `ls -la /`, and you'll notice the /root directory, which might contain the hidden flag. However, are you root? Run `whoami`, and you'll see that you're just "www-data". Next, check your sudo privileges with `sudo -l`, revealing "(ALL) NOPASSWD: ALL"💀.

This indicates that any user can execute all commands as sudo without requiring a password.

Now, execute `sudo ls -la /root`, and you'll find a file named flag.txt. Finally, retrieve the flag with:
```
sudo cat /root/flag.txt
```

The flag is: `picoCTF{wh47_c4n_u_d0_wPHP_5f******`
