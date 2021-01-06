# Snowboard
![1](https://user-images.githubusercontent.com/56958135/103756055-d101a700-5034-11eb-9762-cc29ae939526.png)
<br><br>
In this CTF we are given with a image `Snowboard.jpg`. So we will use `strings` to get the strings associated to it.
<br><br>
Fire `strings Snowboard.jpg` in the terminal.
<br><br>
![2](https://user-images.githubusercontent.com/56958135/103756060-d232d400-5034-11eb-9a73-bf58482bae3f.png)
<br><br>
We can we have a flag `CTFlearn{CTFIsEasy!!!}`. If you will submit it that will not be accepted as flag.
But we can see below that we have a base64 string `Q1RGbGVhcm57U2tpQmFuZmZ9Cg==` so that might we our flag.
<br><br>
So we will decode the above string. Fire `echo Q1RGbGVhcm57U2tpQmFuZmZ9Cg== | base64 -d` in the terminal.
<br><br>
![3](https://user-images.githubusercontent.com/56958135/103756062-d2cb6a80-5034-11eb-8f3b-3adc44295f4a.png)
<br><br>
So we have our flag in the decoded message.
<br><br>
Flag is : `CTFlearn{SkiBanff}`
