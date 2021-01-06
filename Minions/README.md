# Minions
![1](https://user-images.githubusercontent.com/56958135/103757423-c47e4e00-5036-11eb-946b-5ca639f19f9e.png)
<br><br>
In this CTF we are given with image `Hey_You.png`. So first of all we will find all the deatils of the image using [exiftool](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiclYCDiILuAhXbyDgGHVqYAV0QFjAAegQIAhAC&url=https%3A%2F%2Fexiftool.org%2F&usg=AOvVaw3z8pOy1eKETUTVGKAiQeM8).
<br><br>
Fire `exiftool Hey_You.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103757426-c6481180-5036-11eb-8072-36eb012bfef8.png)
<br><br>
We can see there is a warning `Trailer data atfer PNG IEND chunk`. So we will use `strings` to get the strings associated with the image.
<br><br>
Fire `strings Hey_You.png` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/103757431-c6e0a800-5036-11eb-96d2-fcc5c01fcc17.png)
<br><br>
We can see there is a link. Click and download the image `Only_Few_Steps.jpg` from it. Now we will use `binwalk` to see if there is any compressed data in the image.
<br><br>
Fire `binwalk Only_Few_Steps.jpg` in the terminal.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/103757434-c7793e80-5036-11eb-9c58-650a14ef418d.png)
<br><br>
We can see that there is some compressed data in the image so now we will extract it using `binwalk`.
<br><br>
Fire `binwalk --extract --dd='.*' Only_Few_Steps.jpg` in the terminal.
<br><br>
![5](https://user-images.githubusercontent.com/56958135/103757438-c811d500-5036-11eb-9c04-59e92caa0530.png)
<br><br>
Now we will browse to the folder and we can see that there is a RAR file which contains the same image extracted.
<br><br>
![6](https://user-images.githubusercontent.com/56958135/103757443-c8aa6b80-5036-11eb-9a5d-6c6a208f9ec6.png)
<br><br>
So now we know that our flag is somewhere in the extracted image `YouWon(Almost).jpg`.
So we will use `strings` to get the strings associated with the image.
<br><br>
Fire `strings YouWon\(Almost\).jpg`
<br><br>
![7](https://user-images.githubusercontent.com/56958135/103757445-c9430200-5036-11eb-8c7d-9856f0edb829.png)
<br><br>
We can see that there is a string `CTF{VmtaU1IxUXhUbFZSYXpsV1RWUnNRMVpYZEZkYWJFWTJVVmhrVlZGVU1Eaz0=)`. Now we will submit this as a flag it wont accept. There is a statement given in the CTF which states that:
<br><br>
`Hey! Minions have stolen my flag, encoded it few times in one cipher`
<br><br>
So in the above string we have a base64 string `VmtaU1IxUXhUbFZSYXpsV1RWUnNRMVpYZEZkYWJFWTJVVmhrVlZGVU1Eaz0=`. So now we will decode this using [CyberChef](https://gchq.github.io/CyberChef/).
<br><br>
![8](https://user-images.githubusercontent.com/56958135/103757447-ca742f00-5036-11eb-88de-af17c38a0ad3.png)
<br><br>
Now as we know it is encoded many time in same cipher so we will keep it decoding in base64 till we get a meaningful text.
<br><br>
![9](https://user-images.githubusercontent.com/56958135/103757452-cb0cc580-5036-11eb-87c2-68b6755d180b.png)
<br><br>
So now we have a string `M1NI0NS_ARE_C00L`. So we got the message for the flag.
<br><br>
Flag is : `CTFlearn{M1NI0NS_ARE_C00L}`
