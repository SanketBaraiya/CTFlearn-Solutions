# I'm  a dump
![1](https://user-images.githubusercontent.com/56958135/103741662-7e69c000-501f-11eb-9e5b-441e40694db5.png)
<br><br>
In this CTF we are given with a file `file`. So first of all we will use `strings` to get all the strings in the file.
<br<br>
Fire `strings file` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103741669-80338380-501f-11eb-93bf-ebc4664cf52f.png)
<br><br>
We can see that the we have out flag present there `CTFlearnH{fl4ggyfHl4g}H`. But a hint is given in the challenge stating:
<br><br>
`The keyword is hexadecimal, and removing an useless H.E.H.U.H.E. from the flag.`
<br><br>
So we will remove all the `H's` from our flag and we will have our final flag.
<br><br>
Flag is : `CTFlearn{fl4ggyfl4g}`
