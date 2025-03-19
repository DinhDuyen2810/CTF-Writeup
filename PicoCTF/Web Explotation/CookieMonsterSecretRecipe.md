# Description 

Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?
You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:50164/) and good luck

# Hints

Sometimes, the most important information is hidden in plain sight. Have you checked all parts of the webpage?

Cookies aren't just for eating - they're also used in web technologies!

Web browsers often have tools that can help you inspect various aspects of a webpage, including things you can't see directly.

# Solution 

Open `DevTools` on this website, go to the `Application` tab, then navigate to `Cookies`. You will see all stored cookies here, but currently, the list is empty. It seems we need to take some action.

Enter a `username` and `password`, then `login`. You will see the following message:
```
Cookie Monster says: 'Me no need password. Me just need cookies!'

Hint: Have you checked your cookies lately?
```
Go back to the `Cookies` tab, and you will find a cookie named "secret_recipe". Double-click on it and pay attention to its value. Some special characters have been `URL-encoded`, so click "Show URL-decoded".

It looks like a `Base64` string. Copy this value and paste it into [CyberChef](https://gchq.github.io/CyberChef) to decode it and retrieve the flag.


The flag is: `picoCTF{c00k1e_m0nster_l0ves_c00kies_DE*****}`