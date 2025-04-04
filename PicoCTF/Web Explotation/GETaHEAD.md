# Description 

Find the flag being held on this server to get ahead of the competition http://mercury.picoctf.net:28916/

# Hints

Maybe you have more than 2 choices

Check out tools like Burpsuite to modify your requests and look at the responses

# Solution 

First, open the website using the browser built into `Burp Suite`.

You’ll see two options: Red and Blue. When you select one, the website’s color changes accordingly.

Next, go to the `HTTP history` tab. You’ll notice two HTTP requests corresponding to your choices—one using `POST` and the other using `GET`.

This is a hint that you might try using a `HEAD` request. To do this, right-click on either the `GET` or `POST` request, choose `Send to Repeater`, then change the request method to `HEAD` and click `Send`. You’ll receive the flag in the response headers.

Alternatively, you can use a command-line tool like curl to send a HEAD request:

`curl --HEAD http://mercury.picoctf.net:15931/
`

The flag is: `picoCTF{r3j3ct_th3_du4l1ty_70******}`
