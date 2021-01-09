# Blank Page
![1](https://user-images.githubusercontent.com/56958135/104090658-3efcd700-529e-11eb-936b-c8d83653d546.png)
<br><br>
In this CTF we are given with a text file `TheMessage.txt`.If we see the content of the file it's invisible. So we will check the file with hex editor. I am using here
bless hex editor.
<br><br>
Fire `bless TheMessage.txt` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/104090659-40c69a80-529e-11eb-9644-53f0874337a2.png)
<br><br>
We can see that the text file consists of only `.` and `[space]`. At first we will think its a morse code but morse code consists of `.` and `-`. So this is not a
morse code instead its a binary where `. represents 1` and `[space] represents 0`. So to convert the message we will write a python script.
```
file = open("TheMessage.txt", "r").read()
res = ""
for ch in file:
	if ord(ch) == 32:
		res += "0"
	else:
		res += "1"
print(res)
```
<br>Run the pyhton script in the terminal. Fire `python3 filename.py` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/104090660-415f3100-529e-11eb-9e97-6b683ee0a3e1.png)
<br><br>
Copy the binary ouput and convert that into ascii and we will have our flag.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/104090662-41f7c780-529e-11eb-84fa-0e2faa28aa49.png)
<br><br>
Flag is : `CTFlearn{If_y0u_r3/\d_thi5_you_pa553d}`
