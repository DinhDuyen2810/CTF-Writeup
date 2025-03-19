# Description 

Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.
The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.
The website is running `picoCTF News`.

# Hints

Explore backend development with us

The head was dumped.

# Solution 

First, open the DevTools in the browser using Ctrl + U to inspect the page source. We can see some links that might be worth checking:
```
 <script src="https://cdn.tailwindcss.com"></script>
 <a href="/about" class="text-blue-500 hover:underline"> About Us</a>
 <a href="/services" class="text-blue-500 hover:underline"> Services </a>
 <a href="/api-docs" class="text-blue-600 hover:underline">#API Documentation</a> 
```
Additionally, there are some `/img/...` paths that appear to store images.

Next, use `gobuster` to scan the website, but no additional hidden files or directories are found.

Now, visit the first link: `https://cdn.tailwindcss.com`. It contains a lot of information, so press `Ctrl + F` and search for keywords like `flag` or `pico`, but nothing relevant is found. This suggests the flag is not here.

The second and third links yield similar results. However, we should pay attention to `/api-docs` because all other hashtags lack links, except for "#API Documentation".

Exploring the API documentation, we see various commands. Click "Try it out" on any command to see how it functions.

Locate the `GET /heapdump` endpoint and download the file. Open it, press `Ctrl + F`, and search for `pico` to find the flag.

The flag is: `picoCTF{Pat!3nt_15_Th3_K3y_43******}`
