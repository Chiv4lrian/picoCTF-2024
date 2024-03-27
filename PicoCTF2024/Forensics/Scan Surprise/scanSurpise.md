![scan](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/53db2f28-30a8-4fb6-a24f-d0e7bc1cae82)

The challenge itself tells us to inspect what's inside the given qr code.

First, enter the challenge with the given command:

ssh -p 51084 ctf-player@atlas.picoctf.net

Use the password provided by the challenge: 84b12bae

Once connected, a PNG containing the flag will be displayed.
![image](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/e5749e88-a9c3-46c3-be01-a534d22fc848)

To retrieve the flag from the webshell, run the following Linux command:

zbarimg -v flag.png

This will yield the output:
QR-Code:picoCTF{p33k_@_b00_0194a007}
![image2](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/7adbda76-2fb7-4c1a-9ee0-c79980eeb75b)

