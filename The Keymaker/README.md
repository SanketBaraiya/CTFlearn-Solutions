# The Keymaker
![1](https://user-images.githubusercontent.com/56958135/103641379-b1587900-4f77-11eb-9e76-375478455edc.png)
<br><br>
In this CTF we are given with a image The-Keymaker.jpg. So first of all we will find all the deatils of the image using [exiftool](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiclYCDiILuAhXbyDgGHVqYAV0QFjAAegQIAhAC&url=https%3A%2F%2Fexiftool.org%2F&usg=AOvVaw3z8pOy1eKETUTVGKAiQeM8).
If you are using linux install it using `sudo apt install exiftool`.
<br><br>
Fire `exiftool The-Keymaker.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103641384-b289a600-4f77-11eb-945c-adafcd71834c.png)
<br><br>
We can see under the comment flag `CTFlearn{TheKeymakerIsK00l}` but if you will try that it will not work. So now we will find if there are other comments or not.
<br><br>
Fire `file The-Keymaker.jpg` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/103641387-b3223c80-4f77-11eb-8429-833dffe9f202.png)
<br><br>
So we can see there are two base64 strings in the comments. So we will decode that one by one.
<br><br>
Fire `echo b3BlbnNzbCBlbmMgLWQgLWFlcy0yNTYtY2JjIC1pdiBTT0YwIC1LIFNPUyAtaW4gZmxhZy5lbmMg | base64 -d` in the terminal.
<br><br>
![10](https://user-images.githubusercontent.com/56958135/103643269-668c3080-4f7a-11eb-92b2-a4a73270d611.png)
<br><br>
So we found the string `openssl enc -d -aes-256-cbc -iv SOF0 -K SOS -in flag.enc`. So we now know that we need three things to decode flag
<br><br>
`SOF0 (Start Of Frame) key`,<br>
`SOS (Start Of Scan) key` and <br>
`flag.enc file`
<br><br>
Don't worry we will come to the point what is SOS and SOF0, first let us see what the second base64 string gives us.
<br><br>
Fire `echo mmtaSHhAsK9pLMepyFDl37UTXQT0CMltZk7+4Kaa1svo5vqb6JuczUqQGFJYiycY | base64 -d` in the terminal.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/103641392-b4536980-4f77-11eb-90b3-7e214037d4f6.png)
<br><br>
So we can see that it gives a Unicode Text. So this makes us understand this is our flag to be decoded so it is our `flag.enc` so we will store the contents in `flag.enc`.
<br><br>
Fire `echo mmtaSHhAsK9pLMepyFDl37UTXQT0CMltZk7+4Kaa1svo5vqb6JuczUqQGFJYiycY | base64 -d > flag.enc` in the terminal. Then check its content using `cat`.
<br><br>
![5](https://user-images.githubusercontent.com/56958135/103641394-b4ec0000-4f77-11eb-8f0b-19dc85d559b2.png)
<br><br>
Now we need `SOS key` and `SOF0 key`. First We will find out where is the starting of [SOS & SOF0 Key](https://www.ccoderun.ca/programming/2017-01-31_jpeg/).
<br><br>
For SOS
```
SOS
  start of scan
  0xFF 0xDA
  Complicated. See below for details.
```
<br><br>
So we know `SOS` starts as 0xFF 0xDA. So we will open the `The-Keymaker.jpg` in hex editor and select 32 bits after the start of `SOS` as the size of `SOS` is 32 bits.
Use any hex editor u find relavant I m using bless.
<br><br>
Fire `bless The-Keymaker.jpg` in the terminal. Press `Ctrl+f` to find and search `FF DA` and copy 32 bits excluding `FF DA`.
<br><br>
![7](https://user-images.githubusercontent.com/56958135/103641400-b6b5c380-4f77-11eb-8307-82b90c3440b5.png)
<br><br>
Paste the 32 bits strings in any text editor and remove the spaces between them the resultant string would be:
<br>
`000C03010002110311003F00F9766BFC44BEDA8F3F5C031B92CB0E92D6BDC952`
<br><br>
Now we have to do the same with `SOF0`.
<br><br>
For SOF0
```
SOF0 	
  start of frame (baseline DCT)
  0xFF 0xC0
  Variable size. Typically 0x00 0x11 (17 bytes) for images with 3 components (e.g., YCrCb).
```
<br><br>
Now we know `SOF0` starts as 0xFF 0xC0. Repeat the same and find for `FF C0` and copy the string till the next `FF` including `FF C0` and paste it in any text editor and remove `FF C0 00 11` from the pasted string as it defines the size of SOF0.
<br><br>
![6](https://user-images.githubusercontent.com/56958135/103641399-b5849680-4f77-11eb-98f3-bda1a28882fd.png)
<br><br>
The resultant string would be:
<br><br>
`0800BE00C803011100021101031101FF`
<br><br>
Now we have got all the things to decode our flag.enc. Now we will prepare the decoding statement by combining the keys. The statement will be:
<br><br>
`openssl enc -d -aes-256-cbc -iv 0800BE00C803011100021101031101FF -K 000C03010002110311003F00F9766BFC44BEDA8F3F5C031B92CB0E92D6BDC952 -in flag.enc`
<br><br>
Now we will fire the above statement and store the decoded message in `flag or flag.txt` file.
<br><br>
Fire `openssl enc -d -aes-256-cbc -iv 0800BE00C803011100021101031101FF -K 000C03010002110311003F00F9766BFC44BEDA8F3F5C031B92CB0E92D6BDC952 -in flag.enc > flag` in the terminal.
<br><br>
![8](https://user-images.githubusercontent.com/56958135/103641407-b7e6f080-4f77-11eb-97f8-adb8b9f38542.png)
<br><br>
Now we will see the content of `flag or flag.txt` using `cat`.
<br><br>
![9](https://user-images.githubusercontent.com/56958135/103641408-b7e6f080-4f77-11eb-8c3a-471b0fdc819d.png)
<br><br>
So finally we have our flag.
<br><br>
Flag is : `CTFlearn{Ne0.TheMatrix}`
