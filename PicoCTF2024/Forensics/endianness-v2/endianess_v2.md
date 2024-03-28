In this challenge, I initially tried to determine its file type, but to no avail; it appeared to contain only data. Given that the challenge was named "endianess_v2," after some thought, I realized it had something to do with the file's hex representation.

![image](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/c0e0ac55-ab05-4229-b285-e48452ee7179)

Using the command: xxd challengefile

I viewed its binary and analyzed it.

After analyzing the file, I determined that the hex was in little-endian format. 

![image2](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/a3d21e72-1722-4d1b-9c32-6f468207388d)

I then pondered how to read the contents of the file. I deduced that I could either convert it to big-endian or find/create a script that could read this 32-bit system file. I attempted the latter but did not find any script for this purpose. 

Therefore, I searched for the first solution and, to my satisfaction, found it on this forum: https://unix.stackexchange.com/questions/239543/is-there-a-oneliner-that-converts-a-binary-file-from-little-endian-to-big-endian

I used the third answer from that forum, executing the command:

hexdump -v -e '1/4 "%08x"' -e '"\n"' challengefile | xxd -r -p > lastfile

![image3](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/e1f3d2b5-50d0-4865-8908-bab94fff9f7c)

Following this, I used the command: file lastfile

To determine the file type, and I discovered that it was a jpg file.

To download this in the webshell, use the command:

sz [filename]

![image4](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/aa68a5ad-77a7-48c3-bd01-ff888869fad2)

Then, simply change the file format to jpg to view it.

![image5](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/b0876022-dbf2-444d-a17d-c147405022d4)

Flag: picoCTF{cert!f1Ed_iNd!4n_s0rrY_3nDian_6d3ad08e}
