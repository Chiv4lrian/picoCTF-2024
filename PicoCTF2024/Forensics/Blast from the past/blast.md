The challenge requires us to change the date of the specified picture to set the timestamp to a particular date. This means we need to modify all the dates within that jpg to: 1970:01:01 00:00:00.001+00:00.

![image](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/6ce00db1-76b6-437c-8668-a993d3a5cce0)

First, let's determine which dates we should change within the jpg file. We'll run the command:

exiftool original.jpg

![image2](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/97deac1e-cf46-49e9-88e3-04efafbaa384)

![image3](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/9be26126-0140-4a6b-81c9-41cd282ec7d9)

Now that we know which dates to change, I used the following command to achieve this:

exiftool -AllDates='1970:01:01 00:00:00.001' -CreateDate='1970:01:01 00:00:00.001' -DateTimeOriginal='1970:01:01 00:00:00.001' -ModifyDate='1970:01:01 00:00:00.001' -SubSecCreateDate='1970:01:01 00:00:00.001' -SubSecDateTimeOriginal='1970:01:01 00:00:00.001' -SubSecModifyDate='1970:01:01 00:00:00.001' original.jpg

![image4](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/205d5628-4b9b-4d39-9592-ee0abd591a16)

Rename the file to modified.jpg and submit the image to the given netcat:

![image5](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/362fad9e-2c78-4121-9db7-fe4355bb064a)

nc -w 2 mimas.picoctf.net 60045 < modified.jpg

After submitting, I checked if my submission was correct.

The last 7/7 of the checking tag is looking for the Samsung timestamp.

![image6](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/f195f516-b341-412b-bee4-d17ee5236eca)

How can we modify the file to change its Samsung timestamp?

I researched and found these two forums which led me to edit the hex of the modified.jpg and apply the Unix timestamp which is equal to 1970:01:01 00:00:00.001:

https://stackoverflow.com/questions/78185037/how-to-edit-the-samsung-trailer-tag-timestamp

https://stackoverflow.com/questions/3712686/get-hex-time-stamp-from-bash-script

I used the online site: https://www.unixtimestamp.com

![image7](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/83f0a666-834b-4d34-a64f-1f0782c61b5d)

Upon checking the online converter, there were no milliseconds. To solve this, we simply added 01 to the -28800, leading us to 288001.

Next, we converted -288001 to hex using the following command:

hex -28800001
![image9](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/d3ce80fe-f77c-440a-af9a-50b88e9165d2)

This results to: 2d32383830303031

To also set hours, minutes, seconds, and milliseconds to 0, we modify it as:

30 30 30 30 31 00 00 00 00 00 00 00 00

Using a hex editor, we search for UTC to edit the file's Samsung timestamp.
command used : hexeditor [filename]

![433883421_415116257774004_5723479280048312099_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/22e13216-361d-4ea9-b49f-b0b44e1e3ac8)

--to search use ctrl + w and enter UTC--

Upon finding it, in the second line, the data is 310, which is the Samsung timestamp. To change this, we modify some of its bytes using: 30 30 30 30 31 00 00 00 00 00 00 00 00 these bytes

![433960849_2781623375323498_6247843276037207548_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/1e0c0fdc-ba4f-414c-8190-69abd52b5c72)

After making these changes, you can observe that the file's data is now 0001 instead of 310.

![433647623_377318488541060_8254944598448489036_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/4d7c6acd-d69a-4d9c-986f-f6ef3b61dd10)

Submit the modified jpg to the challenge once again and check the flag.

![434002777_965642458489412_337168497252637917_n](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/f3d97903-5cb2-4306-b7ee-0825daa963f9)

Flag: picoCTF{71m3_7r4v311ng_p1c7ur3_83ecb41c}
