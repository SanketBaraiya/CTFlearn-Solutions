# Seeing is believing
![1](https://user-images.githubusercontent.com/56958135/109461267-e7057400-7a87-11eb-800f-97b8aa33e1ce.png)
<br><br>
In this CTF we are given with a zip `message.zip`. So we will unzip the given zip file using `unzip`.
<br><br>
We will fire `unzip message.zip` in the terminal.
<br><br>
Now we can see there is a folder and inside it we have a file `help.me`. Now we will analyze the `help.me` file using `exiftool`.
<br><br>
Fire `exiftool help.me`
<br><br>
![2](https://user-images.githubusercontent.com/56958135/109461287-ec62be80-7a87-11eb-8280-cb8be33dfcf5.png)
<br><br>
We can see in the `File Type` that the type of file is `OGG` ,i.e., it is an audio file. So we will change the extension of the `help.me` file to `help.ogg`.
Simply change the extension by rename.
<br><br>
Now if you we hear the audio file you will nothing but some disturbance. So now we will analyze the audio file using [Sonic Visualiser](https://www.sonicvisualiser.org/download.html).
<br><br>
Fire `sonic-visualiser help.ogg` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/109461295-ee2c8200-7a87-11eb-9641-b1588d5eef36.png)
<br><br>
Now we will check if there is any spectogram or not in the audio file. Goto `Layer > Add Spectogram > All Channels Mixed` or just press `Shift + G`.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/109461297-ef5daf00-7a87-11eb-9cf0-5d08b0d3adad.png)
<br><br>
So we can see that there is a QRCode in the spectogram. So we will scan the QRCode and get redirected to a website where we have our flag.
<br><br>
![5](https://user-images.githubusercontent.com/56958135/109461305-f1c00900-7a87-11eb-891d-490db3c58798.png)
<br><br>
Flag is : `the_flag_is{A_sP3c7r0grAm?!}`
