---
layout: post
title: Linux Keyboard Shortcuts
---

In a terminal:

Keystroke | Full Name | Meaning
--- | --- | ---
Enter | Execute command | Executes the command at the command line
↑ | Most recent shell command | Displays most recent command from your shell history
Ctrl+F | Character forward | Go forward one character
Ctrl+B | Character backward | Go backward one character
Alt+F | Word forward | Go forward one word
Alt+B | Word backward | Go backward one word
Ctrl+A | Beginning of line | Go to the beginning of the current line
Ctrl+E | End of line | Go to the end of the line
Ctrl+L | Clear screen | Clear screen and leave line at the top of the screen
Ctrl+D | Delete current | Delete the current character
Backspace | Delete previous | Delete the previous character
Ctrl+T | Transpose character | Switch positions of current and previous characters
Alt+T | Transpose words | Switch positions of current and previous words
Alt+U | Uppercase word | Change the current word to uppercase
Alt+L | Lowercase word | Change the current word to lowercase
Alt+C | Capitalize word | Change the current word for an initial capital
Ctrl+V | Insert special character | Add special character. For example, to add a Tab character, press Ctrl+V+Tab
Ctrl+K | Cut end of line | Cut text to the end of the line
Ctrl+U | Cut beginning of line | Cut text to the beginning of a line
Ctrl+W | cut previous word | Cut the word located behind the cursor
Alt+D | Cut next word | cut the word following the cursor
Ctrl+Y | Paste recent text | Past most recently cut text
Alt+Y | Paste earlier text | Rotate back to previously cut text and paste it
Ctrl+C | Delete whole line | Delete the entire line

## Command-line completion
**Command, alias, or function:** If the text you type begins with regular characters, the shell tries to complete the text with a command, alias, or function name.
**Variable:** If the text you type begins with a dollar sign ($), the shell completes the text with a variable from the current shell.
**Username:** If the text you type begins with a tilde (~), the shell completes the text with a username. As a result, *~username* indicates the home directory of the named user.
**Hostname:** If the text you type begins with the at symbol (@), the shell completes the text with a hostname taken from the */etc/hosts* file.
