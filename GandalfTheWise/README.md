# GandalfTheWise
![1](https://user-images.githubusercontent.com/56958135/103753976-baa61c00-5031-11eb-897c-48544bc0a437.png)
<br><br>
In this CTF we are given with an image `Gandalf.jpg`. So will use `file` command to see if there are any comments associated with image.
<br><br>
Fire `file Gandalf.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103753978-bc6fdf80-5031-11eb-90ac-c1e67982bdfe.png)
<br><br>
We can clearly see that there are 3 comments which are all base64 encoded. So we will decode them one by one.
<br><br>
Fire `echo Q1RGbGVhcm57eG9yX2lzX3lvdXJfZnJpZW5kfQo= | base64 -d` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/103753982-bd087600-5031-11eb-8513-250020f1dcce.png)
<br><br>
We can see that we got a flag `CTFlearn{xor_is_your_friend}`. If you try to submit this flag it will not accept it. But is does give us a hint that we have to use XOR
But the question is that where? So for that we still have 2 more comments. If you will decode the two base64 string we will get some unicode text so we now know
we have to use that decoded strings and perform XOR on that strings.
<br><br>
For doing this we will write a python script:
```
import base64

string1 = ""
string2 = ""

a = string1
A = base64.b64decode(a)

b = string2
B = base64.b64decode(b)

c = []
l = len(A)

i = 0
while i < l:
  c.append(chr(A[i] ^ B[i]))
  i += 1

print(c)
```
<br><br>
Place the frist base64 string `xD6kfO2UrE5SnLQ6WgESK4kvD/Y/rDJPXNU45k/p` in `string1` variable and `h2riEIj13iAp29VUPmB+TadtZppdw3AuO7JRiDyU` in `string2` variable.
And run the script using `python3 filename.py`.
<br><br>
![4](https://user-images.githubusercontent.com/56958135/103753985-bd087600-5031-11eb-9689-b655242da86d.png)
<br><br>
So we have our flag in the output.
<br><br>
Flag is : `CTFlearn{Gandalf.BilboBaggins}`
