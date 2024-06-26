The challenge tells us to unzip the file mobpsycho.apk.
![image](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/282ebb43-703d-43c2-befe-bab9986610c5)

First, we will unzip the said file with this command:

unzip mobpsycho

Seeing a whole bunch of folders, I thought that the challenge itself wants us to search for the flag inside one of the folders of mobpsycho.

To do this, I used the command to look for all directories of mobpsycho.apk :

grep -irl "pico" /AndroidManifest.xml ./META-INF ./classes.dex ./classes2.dex ./classes3.dex ./res ./resources.arsc

But even after using grep, I didn't see any flag or any small thing that let me know where the flag is. So, I tried to strings the said apk file, copied all of the data, and pasted it in the Notepad to search for the flag.

![image3](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/052c61c3-a146-4fb4-b966-f90633a6fd7a)

After trying different keywords, I finally found something; there is a flag inside the res/color/flag.txt.

So, I read its content with this command:

cat res/color/flag.txt

It gave me this: 7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f62313132616535377d.

This one looks like a hex, so we need to decrypt it to get the flag. 

To decrypt it, we will use this command:

echo -n '7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f62313132616535377d' | xxd -r -p

![image4](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/e1945ad1-fcc0-4f71-b36b-be7a34370f85)

Flag : picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_b112ae57}
