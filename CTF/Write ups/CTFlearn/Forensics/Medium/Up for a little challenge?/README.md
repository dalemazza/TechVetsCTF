
# Up for a little challenge?

* **Author:** Dalemazza
* **Category:** Forensics
* **Points:** 60
* **level:** Medium

## [Challenge](https://ctflearn.com/challenge/142)

* **https://mega.nz/#!LoABFK5K!0sEKbsU3sBUG8zWxpBfD1bQx_JY_MuYEWQvLrFIqWZ0
  You Know What To Do ...**


## Solution

After downloading the file you are given 1 JPG ```Begin Hack.jpg```

First I check the image with ```file Begin Hack.jpg``` This tells you what the file actually is. We can see it is an ```JPEG```.

Lets see if ```strings``` provides anything

A few things of note stick out.

```
flag{Not_So_Simple...}   #This is a false flag
https://mega.nz/#!z8hACJbb!vQB569ptyQjNEoxIwHrUhwWu5WCj1JWmU-OFjf90Prg -N17hGnFBfJliykJxXu8 -
Mp real_unlock_key: Nothing Is As It SeemsU   
password: Really? Again  
```
Browsing to the URL found in the above command gives us a new ```Up For A Little Challenge.zip```

Let's unzip this:
```
unzip 'Up For A Little Challenge.zip' 
Archive:  Up For A Little Challenge.zip
   creating: Did I Forget Again?/
  inflating: Did I Forget Again?/.Processing.cerb4  
   creating: __MACOSX/
   creating: __MACOSX/Did I Forget Again?/
  inflating: __MACOSX/Did I Forget Again?/._.Processing.cerb4  
  inflating: Did I Forget Again?/Loo Nothing Becomes Useless ack.jpg  
  inflating: __MACOSX/Did I Forget Again?/._Loo Nothing Becomes Useless ack.jpg  
  inflating: __MACOSX/._Did I Forget Again?
  ```
Looking at the ```Loo Nothing Becomes Useless ack.jpg``` image with ```binwalk, strings and exitool``` I see nothing that stands out.

If we look back to the ZIP, we can see a file called ```.Processing.cerb4```. This is a hidden file and wil not show up with a normal ```ls```. This is often used in CTF challenges. Always use ```ls -a``` to view unzipped files to check for hidden files. Let's see what this files is

```
file .Processing.cerb4
.Processing.cerb4: Zip archive data, at least v2.0 to extract
```

Okay so this is actually a ```.zip``` file. NEVER trust the extension of a file. ALWAYS CHECK.

Let's make this a ```.zip``` file.

```
mv .Processing.cerb4 .Processing.cerb4.zip
```

Next we open the ZIP.

```
unzip .Processing.zip 
Archive:  .Processing.zip
[.Processing.zip] skycoder.jpg password: 
```

hmmm so this is asking for a password. I admit this took me some time to find!

Recall back to the inital strings this line was in it ```Mp real_unlock_key: Nothing Is As It SeemsU```.

The password for the ZIP is ```Nothing Is As It Seems```

This unzips a ```skycoder.jpg```

Hidden in the corner of the image is the flag.
