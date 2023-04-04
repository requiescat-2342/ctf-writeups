# HideToSee
Cryptography, 100 points
Tags: `Cryptography`

## Description

How about some hide and seek heh?
Look at this image here.

Hints: Download the image and try to extract it.

## Solution

The question provides an image, `atbash.jpg`. 
![alt text](https://github.com/requiescat-2342/ctf-writeups/blob/main/picoctf-2023/HideToSee/atbash.jpg)

The problem was tagged cryptography, which is somewhat misleading and I thought the hint meant I should use binwalk. 
Instead, you're intended to "extract" steganographic data. I used [`steghide`](https://github.com/StefanoDeVuono/steghide). 
Extract the data, leaving the password blank with the following command. 

'''console 
kali@kali:~/picoctf-2023/HideToSee$ steghide extract -sf atbash.jpg 
Enter passphrase: 
wrote extracted data to "encrypted.txt".
'''

`encrypted.txt` contains the text `krxlXGU{zgyzhs_xizxp_1u84w779}`, which looks like an atbash cipher as hinted by the image name.
Putting it into an online tool gives us the flag: `picoCTF{atbash_crack_REDACTED}` 
