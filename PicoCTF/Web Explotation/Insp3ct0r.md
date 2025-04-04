# Description 

Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/41511/` ([link](https://jupiter.challenges.picoctf.org/problem/41511/)) or `http://jupiter.challenges.picoctf.org:41511`

# Hints

How do you inspect web code on a browser?

There's 3 parts

# Solution 

Look at the `How` tab — you’ll see that this website is built using `HTML, CSS, and JavaScript`. You’ll also notice that the flag is split into three parts.

Open DevTools and navigate to the `Sources` tab. There, you’ll find three files. Open each one, one by one, to retrieve all parts of the flag.

The flag is: `picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?8******}`
