# BINWALK

* **Author:** Dalemazza
* **Category:** Forensics
* **Points:** 30
* **level:** Easy

## [Challenge](https://ctflearn.com/problems/108)

* **Here is a file with another file hidden inside it. Can you extract it?**
https://mega.nz/#!qbpUTYiK!-deNdQJxsQS8bTSMxeUOtpEclCI-zpK7tbJiKV0tXY

## Solution

From the name of the challenge we can presume we use the **binwalk** program.

>What is binwalk?
>Binwalk is used to extract embedded data from a file, this can often be an image with a hidden jpg, png within.

Let's see if binwalk finds anything.
```
binwalk PurpleThing.jpg
```
