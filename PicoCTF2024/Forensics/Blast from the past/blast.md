The challenge requires us to change the date of the specified picture to set the timestamp to a particular date. This means we need to modify all the dates within that jpg to: 1970:01:01 00:00:00.001+00:00.

First, let's determine which dates we should change within the jpg file. We'll run the command:

exiftool original.jpg

Now that we know which dates to change, I used the following command to achieve this:

exiftool -AllDates='1970:01:01 00:00:00.001' -CreateDate='1970:01:01 00:00:00.001' -DateTimeOriginal='1970:01:01 00:00:00.001' -ModifyDate='1970:01:01 00:00:00.001' -SubSecCreateDate='1970:01:01 00:00:00.001' -SubSecDateTimeOriginal='1970:01:01 00:00:00.001' -SubSecModifyDate='1970:01:01 00:00:00.001' original.jpg

Rename the file to modified.jpg and submit the image to the given netcat:

nc -w 2 mimas.picoctf.net 60045 < modified.jpg

After submitting, I checked if my submission was correct.

The last 7/7 of the checking tag is looking for the Samsung timestamp.

How can we modify the file to change its Samsung timestamp?

I researched and found these two forums which led me to edit the hex of the modified.jpg and apply the Unix timestamp which is equal to 1970:01:01 00:00:00.001:

https://stackoverflow.com/questions/78185037/how-to-edit-the-samsung-trailer-tag-timestamp

https://stackoverflow.com/questions/3712686/get-hex-time-stamp-from-bash-script

I used the online site: https://www.unixtimestamp.com

Upon checking the online converter, there were no milliseconds. To solve this, we simply added 01 to the -28800, leading us to 288001.

Next, we converted -288001 to hex using the following command:

echo -n "2880001" | xxd -p

This results to: 2d32383830303031

To also set hours, minutes, seconds, and milliseconds to 0, we modify it as:

30 30 30 30 31 00 00 00 00 00 00 00 00

Using a hex editor, we search for UTC to edit the file's Samsung timestamp.

Upon finding it, in the second line, the data is not 0001, which is the Samsung timestamp. To change this, we modify some of its bytes using:

30 30 30 30 31 00 00 00 00 00 00 00 00

After making these changes, you can observe that the file's data is now 0001 instead of 0003.

Submit the modified jpg to the challenge once again and check the flag.

Flag: picoCTF{71m3_7r4v311ng_p1c7ur3_83ecb41c}
