# Description 

Can you get the flag?
Go to this `website` and see what you can discover.

# Hints

How is the password checked on this website?

# Solution 

You can see that this is a sign-in page. Enter the username and password, then log in, and you will receive a 'Log In Failed' message. Go back and open the source code using Ctrl + U, where you will find the following code:

`<form role="form" action="login.php" method="post">`

This means that when you enter your credentials, the website sends the data to `login.php` for verification. Try logging in again, and this time, you will notice:

`<script src="secure.js"></script>`

This indicates that `login.php` calls `secure.js` to validate the username and password. Open `secure.js`, and you will find the correct credentials. Use them to log in again and obtain the flag.

The flag is: `picoCTF{j5_15_7r4n5p4r3n7_05******}`
