The challenge itself ask us to view the file information data. 

Download the file and unzip it. As you can see, it gives us "ukn_reality.jpg". To view its metadata, we will use exiftool and run this command:

exiftool ukn_reality.jpg

After that, we can see its metadata. Looking at the information, we can suspect that the attribution URL is encoded in base64.

To decode it and get the flag, use the command:

echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fYjMyMDQwYjh9Cg==" | base64 -d

Flag: picoCTF{ME74D47A_HIDD3N_b32040b8}
