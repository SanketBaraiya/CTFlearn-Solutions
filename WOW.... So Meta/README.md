# WOW.... So Meta
<br><br>
![1](https://user-images.githubusercontent.com/56958135/103525212-dfb95400-4ea4-11eb-9d33-ec1174d3f483.png)
<br><br>
In this CTF we are giving with a image 3UWLBAUCb9Z2.jpg. So first of all we will find all the deatils of the image using [exiftool](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiclYCDiILuAhXbyDgGHVqYAV0QFjAAegQIAhAC&url=https%3A%2F%2Fexiftool.org%2F&usg=AOvVaw3z8pOy1eKETUTVGKAiQeM8).
If you are using linux install it using `sudo apt install exiftool`
<br><br>
Now we will fire `exiftool 3UWLBAUCb9Z2.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103525216-e0ea8100-4ea4-11eb-960a-38bf21d7166d.png)
<br><br>
In the output find the value of **Camera Serial Number**. The value of it will be our required flag.
<br><br>
```
Creator Tool                    : Photos 1.5
Date Created                    : 2014:12:27 16:45:55
Warning                         : [minor] Fixed incorrect URI for xmlns:MicrosoftPhoto
Camera Serial Number            : flag{EEe_x_I_FFf}
```
<br><br>
So our flag is : `flag{EEe_x_I_FFf}`
