---
title: "Shell-Basics"
datePublished: Sat Oct 26 2024 04:49:16 GMT+0000 (Coordinated Universal Time)
cuid: cm2polsh9000009me67lpaksx
slug: shell-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1731122720948/ee7b1e7a-db55-47ce-8d86-43d4ca9792c9.png
tags: linux, command-line, windows, shell, gui, shell-scripting, cybersecurity, shell-script, shellscripting-bashscripting-filerenaming-automation-devops-linuxcommands

---

What is a shell? A shell is a program on our computer that lets you interact with your operating system. Shell is of two types one is command line which uses human readable commands and the other is graphical user interface.  They’re many different types of shells out there like BASH(Bourne Again SHell), KornShell, command-line etc. To use shell on our computer, we would need a terminal installed on the computer which mostly will already be installed if not it can be downloaded and installed as well.  
When you first launch your terminal, you will see a prompt like the below:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfzPks-0Zh4OmoD2LnzZVhMIDA_dmJq8muTy4onqHJEopOup0-EuBNADbBmm1IknnJBhVo42ZyDqqW1u0tuQ_Ab7JVFBQQmmIxrVW_LAbHErSvVaxMLCpggk3xLOYYLduTrh0VXohOui31YZ0KaFRf4vvY6?key=YL15-wA7vIyYg4PYH64s0g align="left")

This means that the userprofile of the computer sharo and the computer name given is SharonEarnest and the MINGW64 is the version of Git that I’m using. ~ this tells us about the current directory which is the ***home***. $ tells us that I’m not a root user.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdD56FmFDmf3485RA31D0GlQteiZn058Q_YHWwdAd2qWlaSdsCUkhA04C6Sgo-9t2UZ-f9ztjUtmlK7np1H8sdmRadR8I1gwIJH85k69PXkNn3R6Tb6aAlagWVdRkbSd_Pyd5RRJGh5omC1GbN6cm4WigpM?key=YL15-wA7vIyYg4PYH64s0g align="left")

***Echo*** executes the arguments we pass after it. We can use ‘ or “ to have it print a word or argument that has space between them. You can even use escape \\ as well.  
Now how does the shell know how to execute those commands? How does it know that when I type echo followed by something, it should print those arguments? Shell is itself a programming language like Python and it has its own variables, loops and functions. When type a command it means that we are writing a line of code that the shell needs to understand and take action.  Which means when I write a command, it checks the $PATH variable which is called the environment variable. This variable has all the directories listed in it for the shell to look for the programs and run it. So when I type echo it checks the $PATH variable for the command and then executes that program. If it doesn’t find the command then throws an error saying command not found.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdlGYUEaf6ZIDDFvSp1CcM2x9iSp3p6bYHizMB0wewSTjUDX0CtfoZ4qOyWrgK9XvHjOINBhaAqYueyEceeyMK66mWoadVCtrGJgE-b45zRMLd7J2Uu6P7DQmyixUMnfpp90yJ2cssIdf0Klc6h1z4Ed687?key=YL15-wA7vIyYg4PYH64s0g align="left")

These are all the directories that the PATH variable has so when you type a command the shell checks in all of these directories and executes the program to give the output.  
We can also find from which directory the command was executed using the command ***which.*** Also, we can skip for the shell to search the $PATH variable by entering the directory of the command itself.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeHIJ7ZSzVazRj95a7531NH7zvp_8r2MRjucGAoj_yLGdw772vgurPupkU8YeHrrfzK16Iawv63tPJWoRlsdmOa0a5mBYF67CyMDKfn8Nw_ZxYpdj1A0NAe4CER59MICJ7-y-q98FgZKi3KubhJPLsT5wVH?key=YL15-wA7vIyYg4PYH64s0g align="left")

On Linux and macOS the path is separated by a **‘/’** while in windows it is **‘\\’**

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe0lSf7uQ0Icc8uK4og6CAwDgtKPUMkCGOSYnnlsu6z_ds4ceQs342FsCPv7EubAEVR82-d7sY9gXU0i3zEkJ7YmiKHD0c4eL5bVNstIytWOP8FSbjWlxo1c3HlDtkP47DilKjuyA6QOC1ERbeXBK1tZc0c?key=YL15-wA7vIyYg4PYH64s0g align="left")

In Linux and macOS **/** means that all the files and folders are under this root file system.  
In Windows every disk has its own root for an example the **C:\\There are two types of paths: absolute and relative paths.  
Absolute: These start from the root of the systemRelative:** They’re relevant to the current directory  
When we enter ***cd .*** means it refers to the current directory but when we enter ***cd . .*** means it refers to the parent directory.  
**cd .** doesn’t change your location, it lets you stay in the current location only.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXd4R_UTpYiaDhkO97HXKQC_py-EKx9On88nwEfbfbEtGsIatVC4Zmz9joDkzdc19BMs1tU70eFuXSEu3CrnKFwJEr3k1OQw-dWSCkAjhi24cKmex1ac7Hl6pb5WtgU-tjYH6Zm94mIJYsJAgDw1Hn-Q1jtm?key=YL15-wA7vIyYg4PYH64s0g align="left")

**ls** to see what the directory contains.  
**cat**  to see the contents of the file.  
Many commands use flags and options that start with  - that is used to modify their behaviour.  
To see the flags and options that can be used for a particular command we can use the command followed by ***\-h*** or ***\- -help*** command.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeWxXlw9mJWs1z1lK3tJ9dVz0NcH0UaZW_KG0bwwq3510UJbBvxZdE1ue2MctK4dNzHKeqYqEy45uhp-n_oEctmtNJuaMN7Vht2UQVXeyCktGDxkCT9HLKqpYolmkYT7A6uVtm89fPgAthWbPCZl9KuejUs?key=YL15-wA7vIyYg4PYH64s0g align="left")

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcCdUn7cLbv9W48Mkg5Q9PZ8Rx6njybsL2rCF9WerbEqaweJbDntKcGXdcIWnpAD_hMZMJ68NdYPd8_ZJKZexPUeSJghzWpF_XXFG1p3DqQROokXn-t9X6DGH-r6lWpkJq6QGwRtPGEraJqmGs0iI906G_c?key=YL15-wA7vIyYg4PYH64s0g align="left")

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfFvrSu1V46GXj_atOZp0GyehtFavbduIgWSh6Dkw6qxNofUztV22bZm-FmNlXlj8U5btPaA1OK0vtvqVB8Qm9LonbPyo4DbJqubeL9_U3wBiVFvssLacqkokP_A1xXV20qjJavT-oGrqFLpPjphme9KxM?key=YL15-wA7vIyYg4PYH64s0g align="left")

If you notice when I entered the command ***ls*** in the current directory it gave me the list of all the files and folders in that directory but when I used ***ls -l*** command it gave me a long list of the files and directories with their time and date and the permissions as well. Also, we use the command ***ls -a*** command to view the hidden files and folders.

Let’s talk about permissions now. For example when we see drwxer-xr-x 1 for a file or folder. This means that the first letter d indicates that it is a folder and the next 3 set of letters rwx talks about the permissions the owner, group and other users have on that particular folder.  
If the first letter is - then it is a regular file and there are many more indicators like this.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfbXIHKu1xd1Bo6bghFnjxjLQG5JRvYw8uIgB563atyFtpdqNJoyW6kpTYVbvQVtR9A20o2fpLuw02bcbl5fwbI1jVqjjRCMVbQVmTHWdMNoJPJdLlDd62c36czLdFX-iWj8g5Iam9X8yWdOkorkitzzhXG?key=YL15-wA7vIyYg4PYH64s0g align="left")

In the above example, it is a directory. The next 3 sets of letters indicate that rwx, which means the owner of the file has all the access to read(r), write(w) and execute (x) the file. When it comes to r-x this means that the users who are part of the same group as the file or directory have read and execute access only but not write to the file or folder. r-x  means all other users have read and execute access the same as the group members.

**mv** command is used to move the files or rename the files.  
**cp**  command is used to copy a file.  
**mkdir** command is used to create a new directory.  
**man** command gives more information about a command.

\*\*Redirections:

\*\*&gt; you send the output  to a file instead of printing it to the terminal. If the file doesn’t exist, the shell creates it. If it does, the shell overwrites it.  
\&gt;&gt; using this also you send the output to a file instead of printing it to the terminal.  
However, the shell doesn’t overwrite it but appends the output to the last line of the file.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeWpJY-jLWm8XhEIKro_eCu-YLMm_OXNn746HBKcnYAkULqVC-1UOkGgzI-iksiFksa08lf4EqsmHOja_U9zPV6lFc4Y36aUUUuEtoSqzYYXnj_3EJBAUyPhoFkF6JfDPwLoxsuGK1qFRbe1qdbEOfHUd4?key=YL15-wA7vIyYg4PYH64s0g align="left")

&lt; with this you have the input read from a file.  
&lt; &gt; we can combine both input and output redirects which read the contents from one file and add it to the other file. Which basically works like copy and paste.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfobvQPW3jyBugnowToUeYQQlbLAiR3bmBGDXoDqpKwF642qZCK7WRvW0zT3qetXLE83AkvP2LpCRmjTne_HQ68mpBw5QFcxW7rVlL0HEdf0x3Ajq7CKAi5SUHYK33pw58QKZG7_9ADt71zutJlVwNVwQUJ?key=YL15-wA7vIyYg4PYH64s0g align="left")

**Root User:** Root user is a superuser which means they’ve access to all the files to read, write and execute. Since this has a high level of access, logging in as root is not recommended. Instead of performing executions on root directly, we can use **sudo** command to execute the commands as root user.

**/sys:** It is a special folder that has kernel settings as files. Like we can adjust the brightness of the computer using this directory.  For this, that is to make changes to any kernel settings available in this directory when we execute the commands using sudo, even then it will say \*\*permission is denied.  
\*\*

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcCRv_g96oRSE78u4a8MuqkxnmdARNlCwA1WH3FSTojH9zJwFEFffzruEx67iSoPpMKdd4cjWVOfiOLF1MJejQOCut1TqRrHkjzEEi6fccn-niMpqB5rMpC98A8GSfwu5-yF1a9vu3jW9wEzO0SZEALXelL?key=YL15-wA7vIyYg4PYH64s0g align="left")

This is because the redirection operators are executed by the shell itself and not the commands which we use as in the example echo. So, since the shell itself doesn’t run in the superuser mode, it throws the permission denied error when trying to read the brightness file. To resolve this issue we use the command ***tee*** that is used to open the file to write to it and since we will add sudo to it as well, it will execute the command without any error.

**GREP:** It stands for Global Regular Expression Print. It is used to search through text or files for any specific patterns and returns the lines that match.

**Example :** when we type **grep “hello “ hello.txt.** This will search for the word hello in the entire file hello.txt and will print each line that contains that word.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc9_2KxeHlWzsqY8xWq_0mzODDP0or60Pg5Rhqv45xfaaOL4h8f9Ld4euErmGfYolTwMEJIQVeFKtgv4rIxpTJvfALMTy_fV-9V6OBeKFOmq2OjWzvJ6KrYlO94HPejTZpKEdftmqYyHVGbYCUprCcz-Ovl?key=YL15-wA7vIyYg4PYH64s0g align="left")

This command is case sensitive, if we type the above command then it will only print the lines with the word hello in it and not HELLO.

However,using the option **\-i** we can print the Hello irrespective of being case sensitive. Meaning **grep -i “hello” hello.txt** will print hello, HELLO, Hello etc.

Option **\-c** will print the number of lines that contain the word hello in the text file.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdA-moFvslFkO66GXBI-iCpGFvRX111RZ-X7J0bzQpsSFNEYiHAKC2P2ERZw5IMtRyBCDjiSuXZhrG_OgrhWbc0ysFKtwoeF-DIcSC8PdHaYmE94xLTRtdFFMEgXHqkw_-l0VH02s3rJCC3zULMilqb628?key=YL15-wA7vIyYg4PYH64s0g align="left")

Option **\-n** will show each line with the line number where the pattern is found.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdJGYi8fowSEUW42nPWvdQtq621T7kPnuqqFQmdqvZpB-1ED-34gnlRUBkD3tz06RDtolzJfAt9JOfJGQfM-_dXw37r9WjBfK-O9fgdy6cPjNbxpdcSG5loGgFJeqLBagukn5PFyCBYY5Lze_ho3zr_KxM?key=YL15-wA7vIyYg4PYH64s0g align="left")

Option -v will show all the lines except for the pattern you gave as input in the command.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfW6sE2hpBTjMVtkfk3By6ed1xaLKRf_3XHOaY3KDEL8XuQUPavP4tKlMrCgVxAqVC3vvNWIHYRGZ16LzVYjs7ZOUoQdnkzaTOkuGBSe_pZIXqFFZuZmJ31qLxu929VhRWBk4tdqdLu2k5rmjpiNE2VKBJK?key=YL15-wA7vIyYg4PYH64s0g align="left")

Option -r will search for the pattern in all the files and directories in the path that you mentioned and displays the file name and the line where the match is found. If we don’t want to specify the path we can simply type the dot(.) symbol which will indicate it to search in the current directory.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdkjU18uqtrSDuycIhAOBDo3mgGC-Ybh6OgeLsF5NbSU-6RdkAcnRwXM_NPGrx7wARA1UtTBCTI-fSOQ2JWKSOlollXmqQn2VEYb9c-MK28R1NJ4NoSShpjWh8ErXLj733q__l5aDgk3wrtb-GqpJwTuI4y?key=YL15-wA7vIyYg4PYH64s0g align="left")

Option -o will only show the parts of the lines that match the pattern entered and not the entire line.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe386L6UHqpbosyGDVaDkJ3kOS0wMpm0P7FVaCVEcQ9UkDQn1IrZnLkRag156dVNf-tozAREyYwIG6MTvgTCRV4UKiEkBeieaSheoHI7ejUID1mgaDQSCRr6jdCVC56gdRSBwU71iNVbdUJXm8s2NxK6NSq?key=YL15-wA7vIyYg4PYH64s0g align="left")

Option -w will match the entire word in the file and line.  
Egrep will provide all the lines that match either of the pattern entered after the pipe or before the pipe from the file.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcFulnCbMeP5oa5e0QmUqiWLrcMxALncI1bLFGD712uBCfSb-MH5AGVmnx8BT1MFaa7bc5moKrKw3HFwRrgkjtp_IBIdNpKouhhRhUC5jAhvg1_IHZp8aUIKlwaIQpXSh_dxZI3Q7MZsuN2qambF20d42r8?key=YL15-wA7vIyYg4PYH64s0g align="left")

Option -I ignores binary files to prevent unreadable characters from being displayed.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdRjAB7cACBiBKFEmA0g5iHNzc0hdht9ea6Kn1g6mIKTTkJ-HAXplG1u1Go4kW3S880_rU-AK7pDYzkdUAWKRdEjJLUQYSBzq0U1UDPFaLbESnKG8Ik71vE9kUfZyWMPEuyFZAxqWtDthN3F3YUZve1PvxC?key=YL15-wA7vIyYg4PYH64s0g align="left")

***\-A any number***  shows lines after the pattern match. As in if word hello is in the first line, it will show the lines after the line match according to the number u pass after the option -A.  
***\-B any number***  shows lines before the pattern match. As in if word hello is in the third line, it will show the lines before the line match according to the number you have after the option -B.  
***\-C any number*** shows lines before and after the pattern match. As in if word hello is in the third line, it shows the lines before the line match and after the line match according to the number you enter after the option -C.

\*\*Regular expressions in grep

\*\*1)Dot(.) - matches any single character except the new line.  
2)Asterisk (\*): Matches zero or more of the preceding character.  
3)Caret (^): Matches the beginning of a line.  
4)Dollar ($): Matches the end with the pattern you enter.  
5)Brackets (\[\]): Matches any one of the characters in brackets.  
6)Escape Character (\\): Use this to escape special characters.

Grep with pipes: We can combine grep with other commands using pipes |  
Example: ls -l | grep "^d" which will show all the directories in the current directory.  
You can search all multiple files by mentioning the names of it or also just using the asterisk followed by the file type.  
  
***<mark>Important</mark>***  
**Executing a script directly** with ./example.sh requires execute permission.  
**Running a script using an interpreter** like sh example.sh or bash example.sh only requires read permission, as the shell is responsible for executing the commands in the script.