# Description 

Cryptography can be easy, do you know what ROT13 is?

`cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_jdJBFOXJ}`

# Hints

This can be solved online if you don't want to do it by hand!

# Solution 

You can use an online tool to decode this text, but I will teach you another way in Linux.

First, you need to understand what `|` does. It takes the output from the left side and passes it as input to the right side.

Now, the input is the encoded text. You can save it in a file named ROT13.txt and then run:

```
cat ROT13.txt
```

Alternatively, you can use: 
```
echo "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_jdJBFOXJ}"
```

The right side of the pipeline is responsible for decoding. Here, we use tr (translate) as follows:  `tr 'A-Za-z' 'N-ZA-Mn-za-m'`

Now, the full Linux command is:

`cat ROT13.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`

or 

`echo "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_jdJBFOXJ}" | tr 'A-Za-z' 'N-ZA-Mn-za-m'`


The flag is: `picoCTF{next_time_I'll_try_2_rounds_of_rot13_wq******}`
