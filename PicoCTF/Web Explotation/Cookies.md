# Description 

Who doesn't love cookies? Try to figure out the best one. http://mercury.picoctf.net:54219/

# Solution 

You see a text box where you can input something. Try entering `'abcd'` or anything else, and you receive the message: `"That doesn't appear to be a valid cookie."`

Looking at a hidden text that seems like a hint, type it in, and you get: `"That is a cookie! Not very special though..."` But nothing useful appears.

Click `"Home"` and open `DevTools`. Go to the `Application` tab, then click on `Cookies`. You’ll see a cookie named `"name"` with the value `"-1"`.

Now, enter the correct text again, and the cookie value changes to `"0"`. This suggests that the cookie value determines how the webpage behaves.

To test this, go back to the `Home` page, change the cookie value to `"0"`, and refresh `(F5)`. You’ll see that the webpage now looks as if you entered the correct text.

Try increasing the value. When the cookie value reaches `"18"`, you receive the flag.

Alternatively, you can use BurpSuite to brute-force the cookie value:

1. Open the website and enter the correct text.
2. Open the `HTTP history` in the `Proxy` tab and find the POST request when you clicked `"Search"`.
3. Look at the response, where you’ll see a `/check` request.
4. Send `/check` to Intruder, then modify the cookie as `Cookie: name=$0$`.
5. Set the payload type to `Numbers`, with a range from 0 to 30, and start the attack.
6. After the attack completes, check the responses to find the flag, which appears when the value is "18"

The flag is: `picoCTF{3v3ry1_l0v3s_c00k135_96******}`
