---
layout: post
title: Basics keys for emacs
subtitle: some basics keys in emacs
categories: Emacs
tags: [EMACS, TOOLS]
---

# Emacs: Basics keys for emacs

Here are some commonly used keys for *Emacs* operations, which are easy to find and memorize at any time, and can also be used as a learning reference when you first get in touch with *Emacs*.

*Ref : [[Xah Emacs Tutorial]](http://xahlee.info/emacs/index.html)*

## Move the edit cursor

Use the arrow keys ↑ ↓ ← →, and Home, End, PageUp, PageDown keys to move the edit cursor.

| Keyboard Shortcuts     | Actions                             |
| ---------------------- | ----------------------------------- |
| CTRL+ ← or ALT+ b      | Move the cursor left by word.       |
| CTRL+ → or ALT+ f      | Move the cursor right by word.      |
| CTRL+ Home or ALT+ <   | Move to beginning of file           |
| CTRL + End or ALT + >  | Move to end of the file.            |
| CTRL + f or →          | Mover the cursor right by one char. |
| CTRL + b or  ←         | Mover the cursor left by one char.  |
| CTRL+ v or PageDown    | Scroll next page.                   |
| ALT + v or PageUp      | Scroll previous page.               |
| CTRL + u 10 CTRL + n/p | Move forward or backward 10 lines.  |

## Edit the text

| Keyboard Shortcuts       | Actions                                                      |
| ------------------------ | ------------------------------------------------------------ |
| CTRL + x CTRL + f        | Open file or create a new file.                              |
| CTRL + x CTRL + s        | Save the current buffer.                                     |
| CTRL + x k               | Kill the current buffer.                                     |
| ALT + d                  | Delete to the end of the word to the right of the cursor.    |
| ALT + Backspace          | Delete to the beginning of the word to the left of the cursor. |
| CTRL + ALT + Backspace   | Delete the entire line.                                      |
| CTRL + k or ALT + k      | Delete characters from cursor to "end of line".              |
| ALT + k                  | Delete characters from cursor to "end of sentence".          |
| CTRL + w                 | Cut the selected characters.                                 |
| ALT +  w                 | Copy the selected characters.                                |
| CTRL + y                 | Paste the contents of "CTRL + w" or "ALT + w".               |
| CTRL + _                 | Undo.                                                        |
| CTRL + g CTRL + _        | Redo.                                                        |
| CTRL + SPACE or CTRL + @ | Mark the starting point for copy/cut text.                   |
| CTRL + x h               | Select All.                                                  |
| CTRL + s                 | Search Backwards.                                            |
| CTRL + r                 | Search Forwards.                                             |
| CTRL + g                 | To exit search and leave the cursor at the place before search started |

## Replace the characters in current file

1.   Enter the "ALT + %", emacs will prompt you for the find string and replace string. And press " CTRL + ALT + %" can run the "query-replace-regexp"  in current file.
2.   Press "y" to replace, "n" to skip and the " ! " to do all replacement without asking.
3.   Press the "CTRL + g" to cancel the current operation.

## Split window

| Keyboard Shortcuts | Commands                              | Actions                                  |
| ------------------ | ------------------------------------- | ---------------------------------------- |
| CTRL + x 2         | `split-window-below`                  | Split window top/bottom                  |
| CTRL + x 3         | `split-window-right`                  | Split window side by side                |
| CTRL + x 1         | `delete-other-windows`                | Remove all split panes                   |
| CTRL + x 0         | `delete-window`                       | Remove current panel                     |
| CTRL + x o         | `other-window`                        | Move cursor to the other pane            |
| CTRL + x ^         | `enlarge-window/shrink-window`        | Increase /Decrease the height of window. |
| CTRL + x }         | `enlarge-window-horizontally`         | Increase the width of window.            |
| CTRL + x {         | `shrink-window-horizontally`          | Decrease the width of window.            |
| CTRL + x -         | `shrink-window-if-larger-than-buffer` | Shrink the window to fit its content.    |
| CTRL + x +         | `balance-windows`                     | Make all panels same width/height        |

## Buffer management

| Keyboard Shortcuts | Actions                                                      |
| ------------------ | ------------------------------------------------------------ |
| CTRL + x CTRL + b  | List buffers.                                                |
| ALT + x `ibuffer`  | Improved version of list buffers. it colors the file by type. |
| CTRL + x k         | Kill the current buffer.                                     |

#### Make the ibuffer default 

To make  `ibuffer` default, put the following in your .emacs or init.el file:

To make `ibuffer` default, put the following in your init file:

```emacs lisp
(defalias 'list-buffers 'ibuffer) ; make ibuffer default
```

Here's most useful `ibuffer` commands.

-   m → Mark
-   u → Unmark
-   \* u → Mark unsaved
-   S → Save marked buffer
-   D → Close marked buffers

In `ibuffer`, the key sequence * u S D will save all unsaved files and close them. This is particularly useful after you've done a find replace on hundreds of files with `dired-do-query-replace-regexp`.

If you want to switch the buffer, please press "CTRL + x CTRL + b" , and when in the prompt:

-   Tab for name completion.
-   ↑ for previous buffer name you gave. ↓ for next.
-   \* wildcard can be used for part of name. For example, `*k` means any buffer name containing “k”.

