---
layout: post
title: Vim Basics Operator Cheat Sheet
subtitle: some basics keys in vim
categories: VIM
tags: [VIM, TOOLS]
---

#Vim Basics Operator Cheat Sheet        

## Introduction

Vim is a highly configurable text editor built to make creating and changing any kind of text very efficient. It is included as "vi" with most UNIX systems and with Apple OS X. 

 Vim is rock stable and is continuously being developed to become even better. Among its features are:

-   persistent, multi-level undo tree
-   extensive plugin system
-   support for hundreds of programming languages and file formats
-   powerful search and replace
-   integrates with many tools

 **Tip: ** Run vimtutor in a terminal to learn the first Vim commands.  



## Move the edit cursor

| Keyboard or Shortcuts           | Actions                                                      |
| ------------------------------- | ------------------------------------------------------------ |
| `h`                             | Move the cursor back one character.                          |
| `j`                             | Move the cursor to the next line.                            |
| `k`                             | Move the cursor to the previous line.                        |
| `l`                             | Move the cursor forward one character.                       |
| `[number]h/eg: 5h`              | Move the cursor back 5 character.                            |
| `[number]j/eg: 5j`              | Move the cursor to the next 5 line.                          |
| `H`                             | Move the cursor to top of screen.                            |
| `M`                             | Move the cursor to middle of screen.                         |
| `L`                             | Move the cursor to bottom of screen.                         |
| `gg`                            | Move the cursor to the first line of the current file.       |
| `G`                             | Move the cursor to the last line of the current file.        |
| `5gg` or `5G` or `[number]gg/G` | Move the cursor to the line [number]/5 .                     |
| `f + x`                         | Jump to next character of x.                                 |
| `w`                             | Move forwards to the start of a word.                        |
| `e`                             | Move forwards to the end of a word.                          |
| `b`                             | Move backwards to the start of a word.                       |
| `ge`                            | Move backwards to the end of a word.                         |
| `%`                             | % - move to matching character (default supported pairs: '()', '{}', '[]' ) |
| `0`                             | Jump to the start of the current line.                       |
| `$`                             | Jump to the end of the current line.                         |

## Insert mode - inserting/appending text

| Keyboard or Shortcuts | Actions                                             |
| --------------------- | --------------------------------------------------- |
| `i`                   | Start insert before the current cursor.             |
| `I`                   | Start insert at the beginning of current line.      |
| `a`                   | Start insert or append after the current cursor.    |
| `A`                   | Start insert or append at the end of current line.  |
| `o`                   | Append or create a new line below the current line. |
| `O`                   | Append or create a new line above the current line. |
| `ESC`                 | Exit the insert mode.                               |

## Editing the text.

| Keyboard or Shortcuts | Actions                                                      |
| --------------------- | ------------------------------------------------------------ |
| `x`                   | Delete or cut the current character.                         |
| `dd`                  | Delete or cut the current line.                              |
| `ciw`                 | Change or replace entire word.                               |
| `ci"`                 | Change the content inside the double quotes.                 |
| `c$ or C`             | Change or replace from current cursor to the end of the line. |
| `c0`                  | Change or replace from current cursor to the end of the line. |
| `r`                   | Replace  the current single character.                       |
| `u`                   | Undo                                                         |
| `CTRL + r`            | Redo                                                         |
| `yy`                  | Copy or yank the current line.                               |
| `p`                   | Paste the clipboard after cursor.                            |
| `>>`                  | Indent or move right current line one shiftwidth.            |
| `<<`                  | De-indent or move left current line one shiftwidth.          |
| `.`                   | Repeat the last command.                                     |

## Visual mode

| Keyboard or Shortcuts | Actions                                                    |
| --------------------- | ---------------------------------------------------------- |
| `v`                   | Start visual mode and move the cursor to start the marker. |
| `V`                   | Start the linewise visual mode.                            |
| `CTRL + v`            | Start visual block mode.                                   |
| `d`                   | Delete or out the marked content.                          |
| `y`                   | Copy or yank the marked content.                           |
| `u`                   | Change the marked text to lowercase.                       |
| `U`                   | Change the marked text to uppercase.                       |
| `ESC`                 | Exit the current visual mode.                              |

## Search and replace

| Keyboard or Shortcuts | Actions                                                      |
| --------------------- | ------------------------------------------------------------ |
| `/pattern`            | Search forward for pattern .                                 |
| `?pattern`            | Search backward for pattern .                                |
| `\vpattern`           | 'very magic' pattern: non-alphanumeric characters are<br /> interpreted as special regex symbols (no escaping needed). |
| `n`                   | Jump to the next match.                                      |
| `N`                   | Jump to the previous match.                                  |
| `:%s/old/new/g`       | Replace all old with new throughout file.                    |
| `:%s/old/new/gc`      | Replace all old with new throughout file with confirmations. |

## Exiting the vim and save file

| Keyboard or Shortcuts | Actions                                    |
| --------------------- | ------------------------------------------ |
| `:w`                  | Write (save) the file, but don't exit.     |
| `:w !sudo tee %`      | Write out the current file using sudo.     |
| `:wq or :x or ZZ`     | Write (save) and quit.                     |
| `:q`                  | Quit (fails if there are unsaved changes). |
| `:q! or ZQ`           | Quit and throw away unsaved changes.       |
| `:wqa`                | Write (save) and quit on all tabs.         |

## Macros

1). `qa` - record macro and named `a`;          

2). `q` - stop recording macro;

3). `@a` - run macro `a`; 

4). `100@a` - run the macro `a` 100 times.
