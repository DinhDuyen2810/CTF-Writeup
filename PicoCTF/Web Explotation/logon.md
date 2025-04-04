# Description 

The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/44573/` ([link](https://jupiter.challenges.picoctf.org/problem/44573/)) or `http://jupiter.challenges.picoctf.org:44573`

# Hints

Hmm it doesn't seem to check anyone's password, except for Joe's?

# Solution 

Enter any username and password to sign in. It succeeds, but no flag is shown.

Now try using the username Joe, and you’ll see that you can't sign in.

Next, go to the `HTTP history` tab. Look at the first successful login — you’ll notice a `POST` request followed by a `GET` request with a cookie: `admin=False`.

Try changing `admin=False` to `admin=True` in all the requests using the `Repeater`. Then, in the last `GET` request, you’ll receive the flag.

The flag is: `picoCTF{th3_c0nsp1r4cy_l1v3s_0c******}`
