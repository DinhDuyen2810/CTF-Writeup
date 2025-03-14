# Description 

Can you get the real meaning from this file? 

Download the file [here](https://artifacts.picoctf.net/c_titan/3/enc_flag).

# Solution 

To get the file: `wget https://artifacts.picoctf.net/c_titan/3/enc_flag`

Use the `cat enc_flag` command to get the text:  
`YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgya3lNRFJvYTJvMmZRPT0nCg==`

Now you can see this text was encoded in Base64 because of its characteristic padding. You can use an online tool like [CyberChef](https://gchq.github.io/CyberChef) or [Cryptii](https://cryptii.com) to decode it. However, I suggest you use the Linux command:  
```
cat enc_flag | base64 -d
```
 with -d is decode. 
Now you get `b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2kyMDRoa2o2fQ=='`

You know that `b'...'` is how Python represents a byte string. So your job is to decode the remaining part by `echo d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2kyMDRoa2o2fQ== | base64 -d` or use tool to through Base64 decoding again.

Now you have `wpjvJAM{jhlzhy_k3jy9wa3k_i204hkj6}`, looks like a flag. The first thing you can try is Caesar cipher decoding and use [CyberChelf](https://gchq.github.io/CyberChef) and then get the flag

The flag is: `picoCTF{caesar_d3cr9pt3d_b2******}`
