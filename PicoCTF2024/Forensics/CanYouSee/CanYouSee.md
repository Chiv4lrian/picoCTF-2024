The challenge itself ask us to view the file information data. 
![image4](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/169068bd-08cf-47ac-986e-6c43f09c945c)

Download the file and unzip it. As you can see, it gives us "ukn_reality.jpg". To view its metadata, we will use exiftool and run this command:
![image](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/409faf4c-f0e6-4449-8e8c-9473c7b0301b)

exiftool ukn_reality.jpg

After that, we can see its metadata. Looking at the information, we can suspect that the attribution URL is encoded in base64.
![image2](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/4653db9f-b853-47c9-a1ac-faf4af5381b0)

To decode it and get the flag, use the command:

echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fYjMyMDQwYjh9Cg==" | base64 -d
![image3](https://github.com/Chiv4lrian/picoCTF-2024/assets/153472003/03080111-dfa0-49a7-b72f-a0b719cb594a)

Flag: picoCTF{ME74D47A_HIDD3N_b32040b8}
