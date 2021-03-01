# Corrupted File
![1](https://user-images.githubusercontent.com/56958135/109463056-6d22ba00-7a8a-11eb-9328-35c6098c769c.png)
<br><br>
In this CTF we are given with a `unopenable.gif` file. So we will first analyse it using `exiftool`
<br><br>
Fire `exiftool unopenable.gif` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/109463072-73189b00-7a8a-11eb-9747-3e24620d0018.png)
<br><br>
We can see that there is a file format error, i.e., there is something wrong with the header of the file. So to analyze it we will use [bless](http://elinuxbook.com/install-bless-hex-editor-hexadecimal-editor-in-ubuntu-16-04-a-best-hex-editor-for-linux/) hex editor.
<br><br>
Fire `bless unopenable.gif` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/109463076-7449c800-7a8a-11eb-865d-117314819652.png)
<br><br>
As we can see the header of the file is changed. As default header signature of GIF89a is
<br>
`47 49 46 38 39 61`. Find more about signatures on [List Of File Signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)
<br><br>
So now we will insert 8 bits at the staring `47 49 46 38`.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/109463079-757af500-7a8a-11eb-933f-b0c39f0daf2f.png)
<br><br>
Now we can see that the header of the file is GIF89a. Save the file.
## Note
### If you are unable to save the file try using save as and save the file with other name.
<br><br>
Now if you will open the file as it is a gif we can see a animated text. As the speed of the animation is 100ms we are able to read everything. So now we will convert each frames of the gif to png so that we can read it properly.
To do this we will use `imagemagick`.
<br><br>
Fire `convert -coalesce unopenable.gif target.png` in the terminal.
<br><br>
The following command will convert the gif to frames with name `target-{frame_no}.png`.
<br><br>
![5](https://user-images.githubusercontent.com/56958135/109463081-76ac2200-7a8a-11eb-82b7-8888c9704d59.png)
<br><br>
Now if we see the pictures one by one it says
>Decode it ZmxhZ3tnMWZfb3JfajFmfQ==
>
So we have a base64 string which is to be decoded.
<br><br>
Fire `echo ZmxhZ3tnMWZfb3JfajFmfQ== | base64 -d` in the terminal.
<br><br>
![6](https://user-images.githubusercontent.com/56958135/109463083-76ac2200-7a8a-11eb-8a16-6ff5e6cbc873.png)
<br><br>
So we can see that we have our flag.
<br><br>
Flag is : `flag{g1f_or_j1f}`
