---
title: "Variables in Bash Scripting"
datePublished: Sat Nov 09 2024 03:24:23 GMT+0000 (Coordinated Universal Time)
cuid: cm39lqk0o000e09jybupiflis
slug: variables-in-bash-scripting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1731122599326/cb53adf2-3ff5-44ba-982c-eea9cee1f093.png
tags: variables, terminal, bash, scripting, strings, shell-script

---

In Bash scripting, variables allow us to store information for later use, minimizing repetition and enable us to save command outputs directly into variables. For example, the command <mark>file =$(ls)</mark> will execute <mark>ls</mark>, store its output in the <mark>file</mark> variable, and allow us to use it later.

### Declaring Variables

To declare a variable in Bash, simply type the variable name, followed by an equal sign (=) with no spaces, and assign it a value within quotes if it's text or a number. Example: <mark>myname="Sharon". </mark> Variables can contain both strings and numbers.

### Printing Variables

Use the <mark>echo</mark> command to print a variable’s contents by including a dollar sign ($) before the variable name. For example, <mark>echo $myname</mark> will print <mark>Sharon</mark>. The dollar sign is essential to avoid name collisions and to access the variable’s value rather than its name. Keep in mind that variables in Bash aren’t saved once you exit the terminal.

**Example Script to Print Name and Age:**  
<mark>#!/bin/bash<br>myname="Sharon"<br>age="27"<br>echo "My name is $myname."<br>echo "I am $age years old."</mark>  
  
**When executed, this script will print:**  
<mark>My name is Sharon. I am 27 years old.</mark>

### Types of Variables: Manual and Environment Variables

In Bash, there are manually created variables and environment variables. Environment variables are predefined, usually in uppercase, and can be viewed with the <mark>env </mark> command. For better readability, it’s recommended to declare manually created variables in lowercase.  

### Handling Single Quotes Inside Single-Quoted Text

If you need to use single quotes within a single-quoted string, Bash will interpret it as the end of the string. To avoid this, you can either:

1. **Escape the single quote** with a backslash (\\), like so:  
    <mark>echo 'I\'m $age years old'<br>Output : I'm 27 years old.</mark>
    
2. **Use double quotes** for the entire string when it contains single quotes:  
    <mark>echo "I'm $age years old"<br>Output: I'm 27 years old.</mark>