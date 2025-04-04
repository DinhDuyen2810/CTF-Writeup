# Description 

Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/60915/` ([link](https://jupiter.challenges.picoctf.org/problem/60915/)) or `http://jupiter.challenges.picoctf.org:60915`

# Hints

What part of the website could tell you where the creator doesn't want you to look?

# Solution 

The part of a website that prevents bots from indexing it is the `robots.txt` file.

Go to `/robots.txt`, and you’ll see a URL: `/8028f.html`.

Navigate to that URL, and you’ll find the flag.

The flag is: `picoCTF{ca1cu1at1ng_Mach1n3s_8******}`
