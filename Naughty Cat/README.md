# Naughty Cat
![1](https://user-images.githubusercontent.com/56958135/103539603-6169ab80-4ebe-11eb-9495-253b4d2e088e.png)
<br><br>
In this CTF we are given with image cut3_c4t.png. So we will use [binwalk](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiXmeaDsYLuAhUEzjgGHa8TB38QFjAdegQIERAC&url=https%3A%2F%2Ftools.kali.org%2Fforensics%2Fbinwalk&usg=AOvVaw3VqRq3sLfUI8axyRyt-92u) to see if there is any data hidden in the image.
If you are using linux install it using `sudo apt install binwalk`
<br><br>
We will fire `binwalk cut3_c4t.png` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103539612-6595c900-4ebe-11eb-80f4-1f24c954a367.png)
<br><br>
We can see that there is a RAR archive data hidden inside the image.<br>
Now we will fire `binwalk --extract --d='.*' cut3_c4t.png` in the terminal to extract all the data.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/103539614-662e5f80-4ebe-11eb-951d-bb58d63932f8.png)
<br><br>
Then we will use `ls` to verify whether the data is extracted successfully. Then we will use `cd` and go to extracted directory and list out it contents.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/103539617-66c6f600-4ebe-11eb-9617-32aaed20c2a4.png)
<br><br>
Now we can see that there are 2 RAR files and 1 MP3 file in the extracted directory.<br>
First we will open the `28E4B.rar` and see its contents.
<br><br>
![5](https://user-images.githubusercontent.com/56958135/103539621-675f8c80-4ebe-11eb-88f8-f0fc8970b36b.png)
<br><br>
We can see that its the same content as we extracted so if we further extract it we will get in a loop. So now we will see the contents of `y0u_4r3_cl0s3.rar`.
<br><br>
![6](https://user-images.githubusercontent.com/56958135/103539616-66c6f600-4ebe-11eb-8897-44e2876f7560.png)
<br><br>
We can see that nothing is there in the `y0u_4r3_cl0s3.rar` so there might we something hidden inside that. So will we use [exiftool](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiclYCDiILuAhXbyDgGHVqYAV0QFjAAegQIAhAC&url=https%3A%2F%2Fexiftool.org%2F&usg=AOvVaw3z8pOy1eKETUTVGKAiQeM8) 
to get the details of rar file.<br><br>
Fire `exiftool y0u_4r3_cl0s3.rar` in the terminal.
<br><br>
![7](https://user-images.githubusercontent.com/56958135/103539619-675f8c80-4ebe-11eb-945b-14d88f120bbc.png)
<br><br>
So we can see that there is file format error in `y0u_4r3_cl0s3.rar`. So we will match the header signatures of both the RAR files using [xxd](https://www.oreilly.com/library/view/linux-pocket-guide/9781449332969/re25.html).
<br><br>
Fire `xxd -l 12 y0u_4r3_cl0s3.rar` and `xxd -l 12 28E4B.rar` in the terminal.
<br><br>
![8](https://user-images.githubusercontent.com/56958135/103539622-675f8c80-4ebe-11eb-8780-1483f4bd4d93.png)
<br><br>
So we can see that the header signature of the `y0u_4r3_cl0s3.rar` has been changed. As the default header signature of RAR is 
<br>
`52 61 72 21 1A 07 01 00`. Find more about signatures on [List Of File Signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)
<br><br>
Now as we know the header signature is incorrect we will correct it using any hex editor. I am using here [bless](http://elinuxbook.com/install-bless-hex-editor-hexadecimal-editor-in-ubuntu-16-04-a-best-hex-editor-for-linux/) hex editor. 
So using it we will replace the first 16 bits with hex `52 61 72 21 1A 07 01 00`.
<br><br>
![10](https://user-images.githubusercontent.com/56958135/103539627-67f82300-4ebe-11eb-959a-27ac723cc0a8.png)
<br>
![11](https://user-images.githubusercontent.com/56958135/103539637-6a5a7d00-4ebe-11eb-8951-8fee77cd0795.png)
<br><br>
Now we will again check `y0u_4r3_cl0s3.rar`. Now we can see that there is a text file `f1n4lly.txt`. So we will extract the rar file using [unrar](https://www.tecmint.com/how-to-open-extract-and-create-rar-files-in-linux/).
<br>
Fire `unrar x y0u_4r3_cl0s3.rar` in the terminal.
<br><br>
![13](https://user-images.githubusercontent.com/56958135/103539645-6b8baa00-4ebe-11eb-8d90-68ff7cbc4bb1.png)
<br>
![14](https://user-images.githubusercontent.com/56958135/103539647-6c244080-4ebe-11eb-8541-8d755bc9a64d.png)
<br><br>
We can see that the RAR is asking for the password. And we have not yet analysed the `purrr_2.mp3`. Fire `exiftool purrr_2.mp3` in the terminal.
<br><br>
![20](https://user-images.githubusercontent.com/56958135/103545153-2f107c00-4ec7-11eb-9fc6-5848da440354.png)
<br><br>
We can see that under the Artist we find a text `is a password here?`. So we now know that the password is somwhere in the `purrr_2.mp3`.
<br>
So to anaylse it we will use [Sonic Visualiser](https://www.sonicvisualiser.org/download.html).
<br>
Fire `sonic-visualiser purrr_2.mp3` in the terminal.
<br><br>
![15](https://user-images.githubusercontent.com/56958135/103539651-6c244080-4ebe-11eb-8939-38e7ace30d99.png)
<br><br>
Goto `Layer > Add Spectogram > All Channels Mixed` or just press `Shift + G`.
<br><br>
![16](https://user-images.githubusercontent.com/56958135/103539653-6d556d80-4ebe-11eb-96ba-5b6053c4b4d8.png)
<br><br>
So we can see that there is a string `sp3ctrum_1s_y0ur_fr13nd`.
<br>
Now as we have password we will again extract the `y0u_4r3_cl0s3.rar` and enter the passsword string found.
<br><br>
![17](https://user-images.githubusercontent.com/56958135/103539654-6e869a80-4ebe-11eb-923f-44f7ca6ad825.png)
<br><br>
After successfully extracting `f1n4lly.txt`. Open it using any text editor.
<br><br>
![18](https://user-images.githubusercontent.com/56958135/103539657-6f1f3100-4ebe-11eb-86b6-1be6582a7994.png)
<br><br>
Copy the Base64 string i.e.,`ZjByM241MWNzX21hNXQzcg==` and convert that in [CyberChef](https://gchq.github.io/CyberChef/).
<br><br>
![19](https://user-images.githubusercontent.com/56958135/103539658-6f1f3100-4ebe-11eb-9f72-1334861b1223.png)
<br><br>
We have got our flag in the converted string.
<br><br>
Flag is : `f0r3n51cs_ma5t3r`
