# Over the Wire Bandit Write Up

## Introduction

This article is a write-up of the [overthewire bandit wargame](https://overthewire.org/wargames/bandit/). The bandit wargame is a series in the war games on the [Overthewire](https://overthewire.org/wargames/) website that helps one learn Linux from begginers level to expertise. It contains a series of levels, each one a Linux server you log into where you find the password for the next level. 

The Bandit wargame game is free and does not need any subscription fee or payment of any form. You can support the site by [donating](https://overthewire.org/information/donate.html) and here are the [rules to consider while playing the game](https://overthewire.org/rules/).

I have eradicated the passwords for the next levels using this format (***********************)

## Level 0

Link to this level: [https://overthewire.org/wargames/bandit/bandit0.html](https://overthewire.org/wargames/bandit/bandit0.html)

To solve level 0, you need to log into bandit0 with the password **bandit0** using SSH on bandit.labels.overthewrite.org and port 2220.

Connect with ssh by using the following command:

```
ssh bandit0@bandit.labs.overthewire.org -p 222
```

Once it is connected you will see the below output

 ![alt text](images/image.png)


### Common mistakes
I used bandit.labs.overthewire.org while logging in instead of bandit0@bandit.labs.overthewire.org.


>Notice we used bandit0@bandit.labs.overthewire.org and not bandit.labs.overthewire.org while logging in using ssh, this is because we are on level 0 and it will continue throughout the levels. We will attach bandit with the level number and place it before the host bandit.labs.overthewire.org in order to be able to login.

Whenever you find a password for a level, save it in a separate file and use SSH (on port 2220) to log into the next level to continue the game.

> Ps: The port number does not change

###	Command breakdowns
<ul>
<li>ssh – This is a protocol used to securely connect to another computer over a network.</li>
</ul>


## Level 1

Link to this level: [https://overthewire.org/wargames/bandit/bandit1.html](https://overthewire.org/wargames/bandit/bandit1.html)

For this level, you need to find the password located in the readme file in the home directory.


Log into this level by using the below command

```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

The password is the same as level 0: **bandit0**

List out the contents of the file using ls.

`ls`

There is a readme file in it, read out it’s content using cat to find the password.

`Cat`

It will print the following

````python
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ************
````

### Alternative solutions


| Command | Alternatives  |
| -------- | :------: |
| ls     | dir, find    |
| cat     | less     |



###	Command breakdowns
<ul>
<li>ls stands for list and it is used to display the contents of directories.</li>
<li>Cat stands for concatenate and it displays the contents of a file.</li>
</ul>

## Level 2

Link: https://overthewire.org/wargames/bandit/bandit2.html

Log into this level using the below command

```
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

Use the password from the previous level here; the one located in the readme file in level1
List out the content of the directory using ls
Ls
1.	Command breakdowns
The command cat does not work here.  It assumes you are passing something over the standard input. You can read about cat using the commands man cat to see how it interprets a - and press q to exit once done.
Man cat
 Hence, prepending it with a ./.
cat ./-
It will print out the next password
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB

2.	Common mistakes
Not logging out of the previous machine – level0, before logging into level1.
Use the logout commands to logout first before logging into level1.
Logout
Save the password you will use it on level 3

Level 3
Link: https://overthewire.org/wargames/bandit/bandit3.html
Challenge: The password for the next level is stored in a file called --spaces in this filename-- located in the home directory
Log into this level using this command
ssh bandit2@bandit.labs.overthewire.org -p 2220
The password is the one you found on level 2
List out the contents of this directlory using ls
Ls 

Using the same commands as level 2 will not work here and neither will the command cat.
The secret here is to stop option parsing and quote/escape the filename. This can be done by the below command
cat -- "--spaces in this filename--"
1.	Common mistakes
2.	 Alternative solutions
less -- "--spaces in this filename--"
head -- "--spaces in this filename--"
3.	Command breakdowns
--  this tells the terminal “end of options” - that no more command-line options follow
The quotes “” treat the name as a file name instead of different files names because of the spaces in them.
4.	Linux concept learned
Parsing
Argument handling

Save the password and use it on the next level
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME


Level 4
Link: https://overthewire.org/wargames/bandit/bandit4.html
Challenge: The password for the next level is stored in a hidden file in the inhere directory.

Log into this level using this commands and the password from the previous level
ssh bandit3@bandit.labs.overthewire.org -p 2220
List the content of the directory using ls
ls
Enter the inhere directory using the below command
cd
When you list the content of the inhere directory using ls, nothing gets displayed. Hence use ls -a to list all the files in it including the hidden ones
Ls -a
You will find a hidden file called ...Hiding-From-You
Read the content of the hidden file using the same logic as in the previous level

1.	 Alternative solutions
less -- "...Hiding-From-You"
head -- "...Hiding-From-You"
2.	Command breakdowns
ls -a – is used to list all the contens of a directory including the hidden files as is in this case.
3.	Linux concept learned

xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq

Level 5
Link: https://overthewire.org/wargames/bandit/bandit5.html
Challenge: The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Log into this level using these commands and the password from the previous level
ssh bandit4@bandit.labs.overthewire.org -p 2220

listing the contents of the inhere file, you will find the below list:
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09

We need to see the content of all this files and the one that will be human-readable will be our password. remember they all start with a dash hence remember to parse the argument. The easy, but time-consuming way would be to do this by printing the content of each file individually using cat ./<filename>
Cat ./<filename>
However, the best way would be to read the content of all these files all at once and see which one contains a human-readable password. You can use the * to signify all by using this command
cat -- ./-file*
For me file -file07contained the password.
1.	Common mistakes

2.	 Alternative solutions
3.	Command breakdowns
4.	Linux concept learned

6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
Level 6

Link: https://overthewire.org/wargames/bandit/bandit6.html
Challenge: The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
•	human-readable
•	1033 bytes in size
•	not executable

Log into this level using these commands and the password from the previous level
ssh bandit5@bandit.labs.overthewire.org -p 2220

Inside the inhere directory, there are various directories with files inside them and the goal is to find a file that has all the above properties, we can do this by using the find command and specifying the properties. Using the same logic as in level 5, search all the directories using the * to signify all.
You can do this by using different commands each checking for each property then picking the one that meets all of them, such as 

. – signifies inthe current directory
find maybehere* . -size 1033c
find maybehere* . ! -executable
find maybehere* . -type f

Or combining the command into one 
find maybehere* . -type f  -size 1033c ! -executable

Mine is located in ./maybehere07/.file2
You can then cd into that directory and read the contents of file2
1.	Common mistakes
2.	 Alternative solutions
3.	Command breakdowns

size 1033c – checks the files size 
! -executable – checks if the file is not executable
type f – checks if the file is regular – human-readable.

4.	Linux concept learned
Recursive searching

pXa26xhMWaC2SvDotA4r9EgZkulOeSBW
Level 7

Link: https://overthewire.org/wargames/bandit/bandit7.html
Challenge: The password for the next level is stored somewhere on the server and has all of the following properties:
•	owned by user bandit7
•	owned by group bandit6
•	33 bytes in size

Log into this level using this commands and the password from the previous level
ssh bandit6@bandit.labs.overthewire.org -p 2220

We are searching in the root directory blindly for a storage with the above properties, after logging we can use a combines command that checks for all teh properties such as 
find / -user bandit7 -group bandit6 -size 33c
But this gives a long list of files and directories. We can redirect all errors into the null file using the 2>/dev/null in order to eliminate all the results that say “permission denied”
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
Hence the password is found in 
/var/lib/dpkg/info/bandit7.password
You can navigate to the specific file and read the password.

1.	Common mistakes
Assuming it is a file 
Not redirecting the errors to the null file.
2.	 Alternative solutions
3.	Command breakdowns
/ - root directory
-user bandit7 – checks to see if it is owned by bandit7
-group bandit6  - checks to see if it is belongs to the group bandit6
-size 33c – checks for the size
2>/dev/null – redirects the errors to the null file
4.	Linux concept learned

Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
Level 8

Link: https://overthewire.org/wargames/bandit/bandit8.html
Challenge: The password for the next level is stored in the file data.txt next to the word millionth

Log into this level using this commands and the password from the previous level
ssh bandit7@bandit.labs.overthewire.org -p 2220

We need to read the content of the data.txt file and extract the password but when you run cat, the content of the file is too large, hence we need to use grep to find the specific word next to millionth
cat data.txt | grep "millionth"

1.	Common mistakes
2.	 Alternative solutions
3.	Command breakdowns
Grep – it is a command used to search texts inside files.
4.	Linux concept learned
VR1ljMayciFxbnUokuQmJFw6QC9VKtub
Level 9

Link: https://overthewire.org/wargames/bandit/bandit9.html
Challenge: The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

Log into this level using this commands and the password from the previous level
ssh bandit8@bandit.labs.overthewire.org -p 2220

For this challenge we will have to sort the content of data.txt before finding out the line that occurs only once using the below command.
sort data.txt | uniq -u
1.	Common mistakes
Using the cat command, issue is the uniq command does not scan the whole file, only adjacent lines, hence this will not give the correct results.
2.	 Alternative solutions
3.	Command breakdowns
Uniq -u – only prints single occurrences.
Ps: Uniq only works after sorting because it only compares adjacent lines hence the need to start with sorting first.
4.	Linux concept learned

EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
Level 10

Link: https://overthewire.org/wargames/bandit/bandit10.html
Challenge: The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

Log into this level using this commands and the password from the previous level
ssh bandit9@bandit.labs.overthewire.org -p 2220
For this challenge, we need to search for strings inside the data.txt file and make sure it starts with a =, using grep, you can specify the starting part of a search and combine it with the string command.
strings data.txt | grep "^="

1.	Common mistakes
2.	 Alternative solutions
3.	Command breakdowns
String – it prints the human-readable part of the file.
4.	Linux concept learned
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG







