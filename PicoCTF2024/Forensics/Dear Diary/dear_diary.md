The challenge gave us a disk to find a flag within it. 

First we must unzip it and I use the command :

gzip -d disk.flag.img.gz

![433988911_745887737315161_3355389392350723065_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/d251b811-5395-45c7-9df9-3c108853a3ba)

After that I putted the file in the autopsy so i can have a easier look in its contents 

![433949679_3277372199236052_3453579873112956358_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/9b9f95b5-3fc7-4186-9442-d7f4dcfcf17c)

I tried to look at its image details and data unit but i didnt saw smething unusual so i tried to look at its files by searching some keywords in it like pico, flag and txt.

![434013419_920049776579107_7326688965071945663_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/1ece903b-e3ab-4689-83a5-788ebaebcc56)

As I tried it I found that within its txt files there's something usnusual that I see and that is there is a picoCTF with each file but they are in separate manner

![433779163_950046480094337_4500919006521328179_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/36659397-10f0-4eeb-b98d-97ad44af8a59)

![433913696_7095312170597058_6615057057159047500_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/03fcfa45-b7e7-4eeb-b8d8-b95dc28e9cc3)

![434116896_963044478520031_8073012044883351577_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/958e7dad-1a34-4759-99c2-ecff4a44a246)

so i deduced that i will view all of the txt file until I complted the flag.

Flag : picoCTF{1_533_n4m35_80d24b30}
