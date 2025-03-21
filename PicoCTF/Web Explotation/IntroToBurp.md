# Description 

Try `here` to find the flag

# Hints

Try using burpsuite to intercept request to capture the flag

Try mangling the request, maybe their server-side code doesn't handle malformed requests very well.

# Solution 

Open `BurpSuite`, go to the `Proxy` tab, and select `Intercept`. You can configure your `Chrome` browser or use `Open Browser` in `BurpSuite`.

Open the challenge website and enable `Intercept`.
Fill in the registration details and click `Register`.
Switch to `BurpSuite` and check the `HTTP request`. You will see all the transmitted data.

The first request is a `POST` request that sends your input data to the server. Click `Forward` to proceed.
The website then performs a `GET` request. Click `Forward` again, and you'll see an OTP (One-Time Password) input page.
Enter any value for the OTP and click `Submit`. The website sends a `POST` request containing the OTP, and you receive an "Invalid OTP" response.

You can bypass the OTP in two ways:

Modify the HTTP `GET` request to a `POST` request, so you skip the OTP input step entirely and directly receive the flag.

Edit the OTP `POST` request by removing the `otp=` parameter or change to `abc=`, which may trick the server into skipping the OTP check and granting access.


The flag is: `picoCTF{#0TP_Bypvss_SuCc3$S_6b******}`
