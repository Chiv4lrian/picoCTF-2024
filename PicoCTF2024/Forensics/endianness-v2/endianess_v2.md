In this challenge, I initially tried to determine its file type, but to no avail; it appeared to contain only data. Given that the challenge was named "endianess_v2," after some thought, I realized it had something to do with the file's hex representation.

Using the command:

xxd challengefile
I viewed its binary and analyzed it.

After analyzing the file, I determined that the hex was in little-endian format. I then pondered how to read the contents of the file. I deduced that I could either convert it to big-endian or find/create a script that could read this 32-bit system file. I attempted the latter but did not find any script for this purpose. Therefore, I searched for the first solution and, to my satisfaction, found it on this forum: https://unix.stackexchange.com/questions/239543/is-there-a-oneliner-that-converts-a-binary-file-from-little-endian-to-big-endian

I used the third answer from that forum, executing the command:

hexdump -v -e '1/4 "%08x"' -e '"\n"' challengefile | xxd -r -p > lastfile
Following this, I used the command:

file lastfile

To determine the file type, and I discovered that it was a jpg file.

To download this in the webshell, use the command:

sz [filename]

Then, simply change the file format to jpg to view it.

Flag: picoCTF{cert!f1Ed_iNd!4n_s0rrY_3nDian_6d3ad08e}
