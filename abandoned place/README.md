# abandoned place
## Attention
### If you really want to try it yourself and didn't get appropriate hint I prefer you to refer this link [Steganography](https://www.programmersought.com/article/54231957708/). Read the hint given in the CTF and then read out the article on the given link. If still you are not able to solve then refer below solution.
<br><br>
![1](https://user-images.githubusercontent.com/56958135/104118503-acb50b80-534f-11eb-9c11-0fcd59531ead.png)
<br><br>
In this CTF we are given with image `abondoned_street_challenge2.jpg`. First we will see what the image consists.
<br><br>
Fire `eog abondoned_street_challenge2.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/104118504-ade63880-534f-11eb-8b6a-0ce09e355b12.png)
<br><br>
Now as it suggests in the hint `dimensions, dimensions, everything is in dimensions`. So we will find the dimensions of the image.
<br><br>
Fire `exiftool abondoned_street_challenge2.jpg` in the terminal.
<br><br>
```
Image Width     : 2016
Image Height    : 900
```
<br>So now we know the dimensions of image 2016x900. So now we will try and make the dimensions same,i.e., 2016x2016. So we will do that using hex editor. I am using bless hex editor.
<br><br>
To do that we need to find the hex values of 900 and 2016. Use any online converter to convert decimal to hex. Hex values of 900 and 2160 are respectively :
```
03 84
07 E0
```
Fire `bless abondoned_street_challenge2.jpg` in the terminal. Press `Ctrl + f` to find and search for `03 84` and replace it with `07 E0` and save the file.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/104118508-afaffc00-534f-11eb-8025-512497d8c97b.png)
<br><br>
![4](https://user-images.githubusercontent.com/56958135/104118509-b0489280-534f-11eb-84c1-7b089b82ca13.png)
<br><br>
Now we will open the image again and check if we can find our flag in there.
<br><br>
Fire `eog abondoned_street_challenge2.jpg` in the terminal.
<br><br>
![5](https://user-images.githubusercontent.com/56958135/104118510-b0e12900-534f-11eb-8146-317d0395cc06.png)
<br><br>
So we have our flag in the image.
<br><br>
Flag is : `CTFlearn{urban_exploration}`
