---
layout: post
title: Linux Connecting and Expanding Commands
---
# Linux: Connecting and Expanding Commands

You can redirect the input and output of commands in the shell to and from other commands and files. To allow 
commands to be strung together, the shell sues metacharacters. A *metacharacter* is a typed character that has special
meaning to the shell for connecting commands or requesting expansion.

Metacharacters include the pipe character (|), ampersand (&), semicolon (;), right parenthesis ()), left parenthesis ((),
less than sign (<), and greater than sign (>).

## Piping between commands
The pipe (|) metacharacter connects the output from one command to the input of another command. This lets you have one
command work on some data and then have the next command deal with the results. For example,

<pre>
$ <b>cat /etcpasswd | sort | less</b>
</pre>

This command lists the contents of the ```/etc/passwd``` file and pipes the output to the ```sort``` command. The ```sort```
command takes the usernames that begin each line of the ```/etc/passwd``` file, sorts them alphabetically, and pipes the output to the ```less``` command (to page through the output).

## Sequential commands
Sometimes you may want a sequence of commands to run, with one command completing before the next command begins. You can do this by typing several commands on the same command line and separating them with semicolons (;):

<pre>
$ <b>date ; troff -me verylargedocument | 1pr ; date</b>
</pre>

This example formats a huge document and tells you how long it would take. the first command (```date```) showed the date and time before the formatting started. The ```troff``` command formatted the document, then piped the output to the printer. When the formatting was finished, the date and time were printed again.

Another useful command to add to the end of a long command line is ```mail```. You can add the following to the end of a command line.

<pre><b>; mail -s "Finished the long command" chris@example.com</b></pre>

Then, for example, a mail mail message is sent to the user you choose after the command completes.

## Background commands
Some commands can take a while to complete. You can have the commands run in the background by using the ampersand (&).
Text formatting commands (such as ```nroff``` and ```troff```) are examples of commands that are often run in the background to format a large document. You might want to create your own shell scripts that run in the background to check continuously for certain events to occur, such as the hard disk filling up or particular users logging in.
The following is an example of a command being run in the background.

<pre>$ <b>troff -me verylargedocument | lpr &</b></pre>

Just don't close the shell until the process is completed, or that kills the process!!!

## Expanding commands
With command substitution, you can have the output of a command interpreted by the shell instead of by the command itself. In this way, you can have the standard output of a command become an argument for another command. The two forms of command substitution are `$(command)` and `` `command` ``(backticks, not single quotes). The command can include options, metacharacters, and arguments. 

<pre>$ <b>vi $(find /home | grep xyzzy)</b></pre>

This command substitution is dome before the `vi` command is run. First, the `find` command starts at the `/home` directory and prints out all files and directories below that point in the filesystem. The output is piped t othe `grep` command, which filters out all files except for those that include the string `xyzzy` in the filename. Finally, the `vi` command opens all filenaes for editing (one at a time) that include xyzzy.

## Expanding arithmetic expressions
You can pass arithmetic results to a command. There are two forms you can use to expand an arithmetic expression and pass it to the shell: `$[expression]` or `$(expression)`. 

<pre>
$ <b>echo "I am $[2015 - 1957] years old."</b>
I am 58 years old.
</pre>

<pre>
$ <b>echo "There are $(ls | wc -w) files in this directory."</b>
There are 14 files in this directory.
</pre>

## Expanding Variables
Variables that store information within the shell can be expanded using the dollar sign ($) metacharacter. When you expand an environment variable on a command line, the value of the variable is printed instead of the variable name itself. 

<pre>
$ <b>ls -l $BASH</b>
-rwxr-xr-x 1 root  root  1012808 Oct  8 08:53 /bin/bash
</pre>

Using `$BASH` as an argument to `ls -l` causes a long listing of the bash command to be printed.
