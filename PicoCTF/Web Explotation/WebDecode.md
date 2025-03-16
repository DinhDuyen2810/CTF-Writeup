# Description 

Do you know how to use the web inspector?

Start searching `here` to find the flag.

# Hint

Use the web inspector on other files included by the web page.

The flag may or may not be encoded

# Solution 

Select directories sequentially: Home, About, Contact. You don’t see anything related to the flag.

Go back to the first page: Home. 
Press the shortcut `Ctrl + U` to view the page source. You briefly scan through it but don’t find any special strings.

Next, navigate to the second page: About. There, you see the message:
```
Try inspecting the page!! You might find it there
```
This looks like a hint. Press `Ctrl + U`, and you’ll notice the following line:

` <section class="about" notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfZGYwZGE3Mjd9">`
.

It seems to be Base64-encoded. Decode it, and you’ll retrieve the flag.

The flag is: `picoCTF{web_succ3ssfully_d3c0ded_df******}`
