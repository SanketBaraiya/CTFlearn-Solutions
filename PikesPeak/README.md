# PikesPeak
![1](https://user-images.githubusercontent.com/56958135/103752701-0ce63d80-5030-11eb-9d94-9e5356c3118b.png)
<br><br>
In this CTF we are given a image `PikesPeak.jpg`. So we will use `strings` to find all the strings associated to the image.
<br><br>
Fire `strings PikesPeak.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103752703-0e176a80-5030-11eb-9ec7-9d0d5433640b.png)
<br><br>
We can see there are many flags. But there is a hint given in the CTF stating : 
<br><br>
`Pay attentions to those strings`
<br><br>
Now we know that the format of CTFlearn flag is `CTFlearn{some_text}`. So we have to find the string matching exactly like that.
Flag is : `CTFlearn{Gandalf}`
