## Challenge 01 - Credchecker

The first challenge starts with a message:

> Welcome to Flare-On 8! This challenge surves as your tutorial mission for the epic quest you are about to emark upon. Reverse engineer the Javascript code to determine the correct username and password the web page is looking for and it will show you the flag. Enter that flag here to advance to the next stage. All flags will be in the format of valid email addresses and all end with "@flare-on.com".

Upon downloading the attachment we find a html file, asking for a username and password. After inspecting the source code, we see that two checks are performed. If the username is equal to "Admin" and the decoded password is equal to "goldenticket" the flag gets decoded.
The encoding used here is base64. We could try to paste the correct values into the web form, but where is the fun in that?
Writing our own script seems more fun, so here we go:

```
import std/base64
let password_value = cast[seq[char]](encode("goldenticket"))
let key = decode("P1xNFigYIh0BGAofD1o5RSlXeRU2JiQQSSgCRAJdOw==")

var flag = ""
for i in 0..len(key):
  flag = flag & chr(ord(key[i]) xor ord(password_value[i mod len(password_value)]))
echo flag
```
And we find a flag! After submitting it appears to be correct.
