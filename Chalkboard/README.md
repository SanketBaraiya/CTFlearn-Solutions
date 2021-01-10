# Chalkboard
![1](https://user-images.githubusercontent.com/56958135/104117253-d1a48100-5345-11eb-9be2-e9111a2b8965.png)
<br><br>
In this CTF we are given with a image `math.jpg`. So we will use `strings` command to get the strings associated with the image.
<br>
Fire `strings math.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/104117254-d36e4480-5345-11eb-8802-8ddee34850ac.png)
<br><br>
We can find a string which gives a hint to find our flag.
```
CTFlearn{I_Like_Math_x_y}
where x and y are the solution to these equations:
3x + 5y = 31
7x + 9y = 59
```
So we will find the solutions of the above both equations and put them in the flag.
<br><br>
After solving the above equations we will get the following solutions:
```
x = 2
y = 5
```
Flag is : `CTFlearn{I_Like_Math_2_5}`
