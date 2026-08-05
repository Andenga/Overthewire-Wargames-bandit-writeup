# Over the Wire Bandit Write Up

## Introduction

This article is a write-up of the [overthewire bandit wargame](https://overthewire.org/wargames/bandit/). The bandit wargame is a series in the war games on the [Overthewire](https://overthewire.org/wargames/) website that helps one learn Linux from begginers level to expertise. It contains a series of levels, each one a Linux server you log into where you find the password for the next level. 

The Bandit wargame game is free and does not need any subscription fee or payment of any form. You can support the site by [donating](https://overthewire.org/information/donate.html) and here are the [rules to consider while playing the game](https://overthewire.org/rules/).

I have eradicated the passwords for the next levels using this format (***********************)

## Level 0

Link to this level: [https://overthewire.org/wargames/bandit/bandit0.html](https://overthewire.org/wargames/bandit/bandit0.html)

To solve level 0, you need to log into bandit0 with the password **bandit0** using SSH on bandit.labels.overthewrite.org and port 2220.

Connect with ssh by using the following command:

```markdown
ssh bandit0@bandit.labs.overthewire.org -p 222

```
Once it is connected you will see the below output

 ![alt text](images/image.png)


### Common mistakes
I used bandit.labs.overthewire.org while logging in instead of bandit0@bandit.labs.overthewire.org.


>Notice we used bandit0@bandit.labs.overthewire.org and not bandit.labs.overthewire.org while logging in using ssh, this is because we are on level 0 and it will continue throughout the levels. We will attach bandit with the level number and place it before the host bandit.labs.overthewire.org in order to be able to login.

Whenever you find a password for a level, save it in a separate file and use SSH (on port 2220) to log into the next level to continue the game.

> Ps: The port number does not change

###	Command breakdown
<ul>
<li>ssh – This is a protocol used to securely connect to another computer over a network.</li>
</ul>


## Level 1

Link to this level: [https://overthewire.org/wargames/bandit/bandit1.html](https://overthewire.org/wargames/bandit/bandit1.html)

For this level, you need to find the password located in the readme file in the home directory.


Log into this level by using the below command

```markdown
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

Link: [https://overthewire.org/wargames/bandit/bandit2.html](https://overthewire.org/wargames/bandit/bandit2.html)

Log into this level using the below command

```markdown
ssh bandit1@bandit.labs.overthewire.org -p 2220

```
Use the password from the previous level here; the one located in the readme file in level1.

List out the content of the directory using ls

`ls`

###	Common mistakes
I forgot to log out of the previous machine, level0, before logging into level1.

> Use the logout commands to get out of the previous level first before logging into level 1.
> 
> `Logout`


The command cat does not work here. It assumes you are passing something over the standard input. You can read about cat using the commands man cat to see how it interprets a - and press q to exit once done.

`Man cat`

 Hence, when you prepend it with a ./. it will print out the next password

`cat ./-`


## Level 3

Link: [https://overthewire.org/wargames/bandit/bandit3.html](https://overthewire.org/wargames/bandit/bandit3.html)

Log into this level using this command


```markdown
ssh bandit2@bandit.labs.overthewire.org -p 2220

```
The password is the one you found on level 2.

List out the contents of this directlory using ls

`ls` 

Using the same commands as level 2 will not work here and neither will the command cat.

The secret here is to stop option parsing and quote/escape the filename. This can be done using the below command:

```markdown
cat -- "--spaces in this filename--"

```

###	 Alternative solutions

| Command | Alternatives  |
| -------- | :------: |
| cat     | less, head     |
 

###	Command breakdowns
<ul>
<li>--  this tells the terminal “end of options” - that no more command-line options follow</li>
<li>The quotes “” treat the name as a file name instead of different files names because of the spaces in them.</li>
</ul>


## Level 4

Link: [https://overthewire.org/wargames/bandit/bandit4.html](https://overthewire.org/wargames/bandit/bandit4.html)


Log into this level using this command and the password from the previous level

```markdown
ssh bandit3@bandit.labs.overthewire.org -p 2220

```
List the content of the directory using ls

`ls`

Enter the inhere directory using the below command

`cd`

When you list the content of the inhere directory using ls, nothing gets displayed. Hence I used ls -a to list all the files in it including the hidden ones

```markdown
Ls -a
```

You will find a hidden file called ...Hiding-From-You. Read the content of the hidden file using the same logic as in the previous level.

###	Command breakdowns
<ul>
<li>ls -a – is used to list all the contens of a directory including the hidden files as is in this case.</li>
</ul>


## Level 5
Link: [https://overthewire.org/wargames/bandit/bandit5.html](https://overthewire.org/wargames/bandit/bandit5.html)

Log into this level using these commands and the password from the previous level

```markdown
ssh bandit4@bandit.labs.overthewire.org -p 2220

```

listing the contents of the inhere file, you will find the below list:

> -file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09

We need to see the content of all these files and the one that will be human-readable will be our password. Remember, they all start with a dash hence do not forget to parse the argument.

I tried the easy, but time-consuming way, which is to do this by printing the content of each file individually using cat./<filename>

`Cat ./<filename>`

However, the best way would be to read the content of all these files all at once and see which one contains a human-readable password. You can use the * to signify all by using this command:

```markdown
cat -- ./-file*
```

For me, file -file07contained the password.


## Level 6

Link: [https://overthewire.org/wargames/bandit/bandit6.html](https://overthewire.org/wargames/bandit/bandit6.html)


Log into this level using these commands and the password from the previous level

```markdown
ssh bandit5@bandit.labs.overthewire.org -p 2220

```

Inside the inhere directory, there are various directories with files inside them and the goal is to find a file that has all the  properties listed in the query. 

We can do this by using the find command and specifying the properties. Using the same logic as in level 5, search all the directories using the * to signify all.

I first tried using different commands, each checking for a specific property, then picking the one that meets all of them, such as:

> . – signifies in the current directory
> 

```markdown
find maybehere* . -size 1033c
```
```markdown
find maybehere* . ! -executable
```
```markdown
find maybehere* . -type f
```

However, combining the command into one is much easier and faster

```markdown
find maybehere* . -type f  -size 1033c ! -executable

```

Mine is located in ./maybehere07/.file2

You can then cd into that directory and read the contents of file2

### Command breakdowns
<ul>
<li>size 1033c – checks the files size</li>
<li>! -executable – checks if the file is not executable</li>
<li>type f – checks if the file is regular or human-readable.</li>
</ul>


## Level 7

Link: [https://overthewire.org/wargames/bandit/bandit7.html](https://overthewire.org/wargames/bandit/bandit7.html)


Log into this level using this commands and the password from the previous level

```markdown
ssh bandit6@bandit.labs.overthewire.org -p 2220

```

We are searching in the root directory blindly for a storage with the mentioned properties, after logging in, we can use a combination of commands that checks for all the  properties such as:

```markdown
find / -user bandit7 -group bandit6 -size 33c
```

But this gives a long list of files and directories which cannot be scanned quickly by the human eye.

We can redirect all errors into the null file using the 2>/dev/null in order to eliminate all the results that say “permission denied”

```markdown
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

```
Hence the password is found in 

> /var/lib/dpkg/info/bandit7.password

You can navigate to the specific file and read the password.

### Common mistakes
I assumed the mentioned storage was a file and failed to redirect the errors to the null file making my results so large and unreadable.

###	Command breakdowns
<ul>
<li>/ - refers to the root directory</li>
<li>user bandit7 – checks to see if it is owned by bandit7</li>
<li>group bandit6  - checks to see if it is belongs to the group bandit6</li>
<li>size 33c – checks for the size</li>
<li>2>/dev/null – redirects the errors to the null file for a cleaner output</li>
</ul>



## Level 8

Link: [https://overthewire.org/wargames/bandit/bandit8.html](https://overthewire.org/wargames/bandit/bandit8.html)


Log into this level using this commands and the password from the previous level

```markdown
ssh bandit7@bandit.labs.overthewire.org -p 2220

```

We need to read the content of the data.txt file and extract the password, but when you run the cat command, the contents of the file is too large.

Hence we need to use grep and specify out search to find the specific word next to millionth.

```markdown
cat data.txt | grep "millionth"

```

## Level 9

Link: [https://overthewire.org/wargames/bandit/bandit9.html](https://overthewire.org/wargames/bandit/bandit9.html)


Log into this level using this commands and the password from the previous level

```markdown
ssh bandit8@bandit.labs.overthewire.org -p 2220

```
For this challenge, we will have to sort the content of data.txt first before finding out the line that occurs only once using the below command.

```markdown
sort data.txt | uniq -u

```
###	Common mistakes
Using the cat and uniq command, issue is the uniq command does not scan the whole file, only adjacent lines, hence this will not give the correct results.

### Commands breakdown
<ul>
<li>Uniq -u – only prints single occurrences.</li>
</ul>

> Ps: Uniq only works after sorting because it only compares adjacent lines hence the need to start with sorting first.

## Level 10

Link: [https://overthewire.org/wargames/bandit/bandit10.html](https://overthewire.org/wargames/bandit/bandit10.html)


Log into this level using this commands and the password from the previous level

```markdown
ssh bandit9@bandit.labs.overthewire.org -p 2220

```
For this challenge, we need to search for strings inside the data.txt file and make sure it starts with an equal sign, =. 

Using grep, you can specify the starting part of a search and combine it with the string command.

```markdown
strings data.txt | grep "^="

```

###	Command breakdown
<ul><li>String – it prints the human-readable part of the file.</li></ul>









