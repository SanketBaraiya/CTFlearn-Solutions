# PDF by fdpumyp
![1](https://user-images.githubusercontent.com/56958135/104091491-b8e38f00-52a3-11eb-8ea6-aee8747e4f79.png)
<br><br>
In this CTF we are given with a pdf file `dontopen.pdf`. So we will use `strings` command to find the strings asscociated with it.
<br><br>
Fire `strings dontopen.pdf` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/104091492-baad5280-52a3-11eb-8615-50d57eb77638.png)
<br><br>
We can see there are two base64 encoded strings so we will decode them.
<br>
Fire `echo Q1RGbGVhcm57KV8xbDB3M3kwVW0wMG15MTIzfQ== | base64 -d` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/104091493-bb45e900-52a3-11eb-98d7-5a72cd65c05c.png)
<br><br>
So we have our flag in the encoded string.
<br><br>
Flag is : `CTFlearn{)_1l0w3y0Um00my123}`
