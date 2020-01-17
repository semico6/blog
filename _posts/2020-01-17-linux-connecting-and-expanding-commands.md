---
layout: post
title: Linux: Connecting and Expanding Commands
---

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
