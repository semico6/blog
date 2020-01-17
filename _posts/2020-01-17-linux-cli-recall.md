---
layout: post
title: CLI recall commands
---

Taken from: Linux Bible

After you type a command line, the entire command line is saved in your shell's history list. This list is stored in the 
current shell until you exit the shell. After that, it is written to a history file, from which any command can be recalled 
to run again at your next session. After a command is recalled, you can modify the command line, as described earlier.

To view your history list, use the `history` command. Type the command without options or followed by a number to list that
many of the most recent commands. For example,

<pre>
$ <b>history 8</b>
382 date
383 ls /usr/bin | sort -a | more
384 man sort
385 cd /usr/local/bin
386 man more
387 useradd -m /home/chris -u 101 chris
388 passwd chris
389 history 8
</pre>

You can use the history command output in a few ways:
- ```!n``` -Run command number. Replace the ```n``` with the number of the command line and that line is run. 
<pre>
$ <b>!382</b>
dateWed Oct 29 21:30:06 PDT 2014
</pre>
- ```!!``` -Run previous command. 
<pre>
$ <b>!!</b>
dateWed Oct 29 21:30:39 PDT 2014
</pre>
- ```!?string?``` -Run command containing string. This runs the most recent command that contains a particular
string of characters.
<pre>
$ <b>!?dat?</b>
dateWed Oct 29 21:32:41 PDT 2014
</pre>

## Other methods of using command history
Key(s) | Function Name | Description
--- | --- | ---
Arrow up/down | Step | Press the up and down arrow keys to step through each command line in your history
Ctrl+R | Reverse incremental search | After you press these keys, you enter a search string to do a reverse search. As you type the string, a matching command line appears that you can run or edit.
Ctrl+S | Forward incremental search | This is the same as the preceding function but for forward search
Alt+P | Reverse search | After you press these keys, you enter a string to do a reverse search. type a string and press Enter to see the most recent command line that includes that string.
Alt+N | Forward Search | This is the same as the preceding function but for forward search.

You can also work with your history list by using the ```fc``` command. type **fc** followed by a history line number, and that command line is opened in a text editor (vi by default). Make the changes you want, save and exit the text editor, and the command runs.
You can also give a range of lines you wish ```fc``` to run, such as ```fc 100 105```.
After you close your shell, the history list is stored in the ```.bash_history``` file in your home directory. Up to 1,000 history commands are stored for you by default.
