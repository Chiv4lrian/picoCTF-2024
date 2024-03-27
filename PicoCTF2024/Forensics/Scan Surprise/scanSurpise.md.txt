First, enter the challenge with the given command:

ssh -p 51084 ctf-player@atlas.picoctf.net

Use the password provided by the challenge: 84b12bae

Once connected, a PNG containing the flag will be displayed.

To retrieve the flag from the webshell, run the following Linux command:

zbarimg -v flag.png

This will yield the output:
QR-Code:picoCTF{p33k_@_b00_0194a007}
