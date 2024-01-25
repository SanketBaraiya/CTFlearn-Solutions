# Python Reversal
<img width="486" alt="2024-01-25 12_38_33-Challenge - Python Reversal - CTFlearn - CTF Practice - CTF Problems - CTF Chall" src="https://github.com/SanketBaraiya/CTFlearn-Solutions/assets/56958135/a5584e30-8076-4a44-9f03-63234737364d"><br><br>
In this challenge we are given with a `rev.py` . The aim of the challenge is to reverse the python code to get the flag. Upon thorough analysis of the code we can see that the flag goes through three steps, i.e., `obfuscate` , `crypt` , `mikeSwift` .
<br><br>
And then it is matched with a string given below which we can say that is the flag but an encrypted flag:<br>
> 81h4ck891h4ck931h4ck3l1h4ckl81h4ck821h4ck2j1h4ckj81h4ck811h4ck1y1h4cky81h4ck801h4ck061h4ck671h4ck791h4ck951h4ck571h4ck781h4ck8y1h4cky71h4ck771h4ck761h4ck671h4ck761h4ck6y1h4cky71h4ck751h4ck5t1h4ckt71h4ck741h4ck4h1h4ckh71h4ck731h4ck3d1h4ckd71h4ck721h4ck2f1h4ckf71h4ck711h4ck1g1h4ckg71h4ck701h4ck0f1h4ckf61h4ck691h4ck9g1h4ckg61h4ck681h4ck8f1h4ckf61h4ck671h4ck7d1h4ckd61h4ck661h4ck6f1h4ckf61h4ck651h4ck551h4ck561h4ck641h4ck441h4ck461h4ck631h4ck331h4ck361h4ck621h4ck241h4ck461h4ck611h4ck131h4ck361h4ck601h4ck051h4ck551h4ck591h4ck9=1h4ck=51h4ck581h4ck801h4ck051h4ck571h4ck7n1h4ckn51h4ck561h4ck6R1h4ckR51h4ck551h4ck5s1h4cks51h4ck541h4ck4R1h4ckR51h4ck531h4ck3z1h4ckz51h4ck521h4ck2Z1h4ckZ51h4ck511h4ck1f1h4ckf51h4ck501h4ck0V1h4ckV41h4ck491h4ck9T1h4ckT41h4ck481h4ck8M1h4ckM41h4ck471h4ck7f1h4ckf41h4ck461h4ck6N1h4ckN41h4ck451h4ck5H1h4ckH41h4ck441h4ck4Z1h4ckZ41h4ck431h4ck3y1h4cky41h4ck421h4ck2R1h4ckR41h4ck411h4ck1z1h4ckz41h4ck401h4ck0d1h4ckd31h4ck391h4ck9r1h4ckr31h4ck381h4ck8N1h4ckN31h4ck371h4ck7G1h4ckG31h4ck361h4ck6N1h4ckN31h4ck351h4ck5i1h4cki31h4ck341h4ck491h4ck931h4ck331h4ck311h4ck131h4ck321h4ck2Z1h4ckZ31h4ck311h4ck101h4ck031h4ck301h4ck0w1h4ckw21h4ck291h4ck9m1h4ckm21h4ck281h4ck8R1h4ckR21h4ck271h4ck771h4ck721h4ck261h4ck6J1h4ckJ21h4ck251h4ck5X1h4ckX21h4ck241h4ck4Z1h4ckZ21h4ck231h4ck3i1h4cki21h4ck221h4ck2l1h4ckl21h4ck211h4ck131h4ck321h4ck201h4ck0Y1h4ckY11h4ck191h4ck971h4ck711h4ck181h4ck871h4ck711h4ck171h4ck741h4ck411h4ck161h4ck651h4ck511h4ck151h4ck561h4ck611h4ck141h4ck451h4ck511h4ck131h4ck341h4ck411h4ck121h4ck2t1h4ckt11h4ck111h4ck1e1h4cke11h4ck101h4ck0f1h4ckf91h4ck9E1h4ckE81h4ck8U1h4ckU71h4ck7I1h4ckI61h4ck6F1h4ckF51h4ck5S1h4ckS41h4ck4r1h4ckr31h4ck3o1h4cko21h4ck2l1h4ckl11h4ck1f1h4ckf01h4ck0

So to proceed we need to reverse the flow. So we will first analyse what the `mikeSwift` function does. On analysing, we can say that the `mikSwift` function is appending `some_value h4ck some_value`. So we will remove all the apperances of that particular instances. This can be done in many many you can write a python code or just find and replace. What I did is I copy and pasted the string to code editor and replace all the instances with blank.
<br><br>
*Note: Make sure to remove the characters before and after the h4ck.*
<br><br>
This is how the string looks after the reversing of first function:<br>
> 893l82j81y80679578y77676y75t74h73d72f71g70f69g68f67d66f65564463362461360559=58057n56R55s54R53z52Z51f50V49T48M47f46N45H44Z43y42R41z40d39r38N37G36N35i34933132Z31030w29m28R27726J25X24Z23i22l21320Y19718717416515614513412t11e10f9E8U7I6F5S4r3o2l1f0

Now we will analyse the next function, i.e., `crypt` . On analysing it we came to know that this function is adding a counter after each character of string and then they are reversing it. so we can remove the counter manually or programatically. Which should result in following string:<br>
> 893ljy65y6ythdfgfgfdf543435=0nRsRzZfVTMfNHZyRzdrNGNi91Z0wmR7JXZil3Y7745654tefEUIFSrolf

Also we observe that it is adding a 893 at the start so we will also remove it and then reverse the string which will result in:<br>
> florSFIUEfet4565477Y3liZXJ7Rmw0Z19iNGNrdzRyZHNfMTVfZzRsRn0=534345fdfgfgfdhty6y56yjl

Now we will move on to the last function, i.e., `obfuscate` . On analysing it we came to know that it is sandwiching the actual string between two strings, i.e., `florSFIUEfet4565477` & `534345fdfgfgfdhty6y56yjl` . After removing both we get:<br>
> Y3liZXJ7Rmw0Z19iNGNrdzRyZHNfMTVfZzRsRn0=

We can see that the string is base64 encoded so we will decode that and we will get our flag.<br><br>
Flag is: `cyber{Fl4g_b4ckw4rds_15_g4lF}`
