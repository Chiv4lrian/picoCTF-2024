The challenge itself ask us to search for a file that has the same checksum that is inside the checksum.txt which is: 3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4
![image](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/e4c510cc-9168-47c3-a501-936a6ac7ca23)

First, enter the challenge with the given command: 

ssh -p 54282 ctf-player@rhea.picoctf.net

Use the password provided by the challenge: 84b12bae

After entering the challenge, use the command: ls to view the server contents.

To see checksums of files in the files folder, run:

cd files
sha256sum *
![image2](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/63bffbdb-5788-402f-bb68-c96d4e2cfb02)

Copy the checksums to a text file, then use Ctrl + F to find the matching checksum in checksum.txt.
![image3](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/1589fed7-3f6b-4809-aade-7d5f98574a88)

![image4](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/aedf752e-e5ff-47a9-87b9-79df5b12fae4)

For example, the file e018b574 matches a checksum. View its hash with:

cat e018b574

The hash is: Salted__muI8ݯ;ZqE+LG(%Al6q?k$qE

Finally, decrypt the hash:

./decrypt.sh files/e018b574

The flag is: picoCTF{trust_but_verify_e018b574}

