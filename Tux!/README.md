# Tux!
![1](https://user-images.githubusercontent.com/56958135/104117430-36141000-5347-11eb-8c39-0a9f394f3116.png)
<br><br>
In this CTF we are given with a image `Tux.jpg`. So we will use `binwalk` to see is there any data compressed inside the image.
<br><br>
Fire `binwalk Tux.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/104117432-36aca680-5347-11eb-843c-7535a6dbc2ef.png)
<br><br>
So we can see there is a ZIP file compressed inside the image. So now we will extract that data.
<br><br>
Fire `binwalk --extract --dd='.*' Tux.jpg` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/104117433-37ddd380-5347-11eb-8361-0dd430edbd0b.png)
<br><br>
So we can see there is a zip file in the extracted directory. If you will try to unzip it , it will ask for a password. So now we need to find password to unzip the zip file.
<br><br>
So we will use `exiftool` to get all the details realated to the image.
<br><br>
Fire `exiftool Tux.jpg` in the terminal.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/104117434-38766a00-5347-11eb-8f4d-4fe7a7372db8.png)
<br><br>
We can see there is a base64 string in the comment copy that string and decode it. We will get the following after decoding base64:
```
Password: Linux12345
```
<br>Now we will use `unzip` command to unzip the zip file and enter password when prompt. And see the content of the extarcted file.
<br><br>
Fire `unzip 1570.zip` in the terminal.
<br><br>
![5](https://user-images.githubusercontent.com/56958135/104117435-390f0080-5347-11eb-9e3b-e0bde0d1f57a.png)
<br><br>
We can see we have our flag in the extracted file.
<br><br>
Flag is : `CTFlearn{Linux_Is_Awesome}`
