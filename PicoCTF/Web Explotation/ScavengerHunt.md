# Description 

There is some interesting information hidden around this site http://mercury.picoctf.net:27278/. Can you find it?

# Hints

You should have enough hints to find the files, don't run a brute forcer.

# Solution 

The "What" page states that this site is built using `HTML, CSS, and JS`.

Open `DevTools` and navigate to the `Sources` tab to view all files.

In the HTML file, you find the first part of the flag:

`<!-- Here's the first part of the flag: picoCTF{t -->`

In the CSS file, another part of the flag is present:

`/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */`

In the JS file, you find a message:

`/* How can I keep Google from indexing my website? */`

This suggests using a [robots.txt](https://developers.google.com/search/docs/crawling-indexing/robots/intro?hl=vi) file, which prevents search engines from indexing certain pages.

Visit http://mercury.picoctf.net:27278/robots.txt, and you get the third part of the flag:

`Part 3: t_0f_pl4c. I think this is an Apache server... can you Access the next flag?`

The hint suggests something related to `"Apache server"` and `"Access"`, leading to `.htaccess`.

Go to http://mercury.picoctf.net:27278/.htaccess, where you find:

`Part 4: 3s_2_lO0k. I love making websites on my Mac, I can Store a lot of information there.`

This suggests a connection to Mac-related storage, specifically `.DS_Store`.

Visit http://mercury.picoctf.net:27278/.DS_Store, and you retrieve the final part of the flag:

`Congrats! You completed the scavenger hunt. Part 5: _a69684fd}`

---
Alternatively, you can use [gobuster](https://github.com/DinhDuyen2810/CTF-Writeup/blob/main/PicoCTF/Web%20Explotation/n0s4n1ty1.md) to scan for hidden files and directories. Running the command reveals the following results:
```
/.DS_Store            (Status: 200) [Size: 62]
/.htaccess            (Status: 200) [Size: 95]
/index.html           (Status: 200) [Size: 961]
/robots.txt           (Status: 200) [Size: 124]
```

The flag is: `picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_a6******}`
