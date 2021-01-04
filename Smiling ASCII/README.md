# Smiling ASCII
<br><br>
![1](https://user-images.githubusercontent.com/56958135/103520235-daf0a200-4e9c-11eb-886d-b2440d7c30f4.png)
<br><br>
So in this CTF we are given with an smiling.png. So fisrt we will find out all the details of given image using [exiftool](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiBk9z-_IHuAhW3zDgGHYA5B3wQFjAAegQIARAC&url=https%3A%2F%2Fexiftool.org%2F&usg=AOvVaw3z8pOy1eKETUTVGKAiQeM8).If you are using linux install it using `sudo apt install exiftool` .
<br><br>
Now we will fire `exiftool smiling.png` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103521371-a54cb880-4e9e-11eb-8365-9b586d1ff3b0.png)
<br><br>
Now we can see that the is a warning **[minor] Trailer data after PNG IEND chunk.** So we know that there is some data after the IEND (which marks the end of the image data).
<br><br>
Now to extraxt that data we will use [zsteg](https://www.aldeid.com/wiki/Zsteg). By firing `zsteg --all smiling.png` in the terminal we get our flag.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/103522362-48520200-4ea0-11eb-8cb6-adbce4acd6d1.png)
<br><br>
So our flag is : `CTFlearn{ascii_pixel_flag}`
