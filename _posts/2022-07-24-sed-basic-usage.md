---
layout: post
title: Some Basic Usage of Sed
subtitle: Sed - A tool for line-oriented text processing
categories: LINUX
tags: [SED, LINUX]
---

# SED BASIC USAGE

![image](https://linuxhandbook.com/content/images/2020/07/sed-commands-featured.jpeg)

## Introduction of seed
Sed is a non-interactive context editor that runs on the UNIX operating system. Sed is designed to be especially useful in three cases:
1.  To edit files too large for comfortable inter- active editing;
2.  To edit any size file when the sequence of editing commands is too complicated to be comfortably typed in interactive mode;
3.  To perform multiple 'global' editing functions efficiently in one pass through the input.

## The baic usage
### *1 . Basic text substitution using 'sed'*
Any particular part of a text can be searched and replaced by using searching and replacing pattern by using `sed` command. In the following example, ‘s’ indicates the search and replace task. The word ‘Bash’ will be searched in the text, “Bash Scripting Language” and if the word exists in the text then it will be replaced by the word ‘Perl’.

``` bash
$ echo "Bash Scripting Language" | sed 's/Bash/Perl/'
```
**Output:**
```
Perl Scripting Language
```

The word, ‘Bash’ exists in the text. So the output is ‘Perl Scripting Language’.


### *2. Replace all instances of a text in a particular line of a file using ‘g’ option*
The ‘g’ option is used in `sed` command to replace all occurrences of matching pattern. Create a text file named **sed.txt** with the following content to know the use of ‘g’ option. This file contains the word. **‘sed.txt’** multiple times.

```
# the content of sed.txt
sed is a wonderful tools of text editing.
sed is powerful. sed is a powerful line editor. sed ...
sed is easy to learn.
```
Using the following command to replace all occurrences of 'sed' in the second line of the file.
``` bash
sed '2 s/sed/awk/g' sed.txt
```
**Output:**
```
sed is a wonderful tools of text editing.
awk is powerful. awk is a powerful line editor. awk ...
sed is easy to learn.
```
If you want to replace all occurrences of 'sed' in the file, you can using the following command.
``` bash
sed 's/sed/awk/g' sed.txt
```

### *3. Replace the second or third occurrence only of a match on each line*
If any word appears multiple times in a file then the particular occurrence of the word in each line can be replaced by using `sed` command with the occurrence number. The following **sed.txt**
```bash
sed 's/sed/awk/g2' sed.txt
```
**Output:**
```
sed is a wonderful tools of text editing.
sed is powerful. awk is a powerful line editor. sed ...
sed is easy to learn.
```
### *4. Replace the last occurrence only of a match on each line*
Create a file called **sed-test.txt** with the content shown below:
```
Aaa String, Bbb String, Ccc String, Ddd String, E String.
A Character, B Character, C Character, D Character, E Character.
```

``` bash
sed 's/\(.*\)String/\1Character/' lang.txt
```
**Output:**
```
Aaa String, Bbb String, Ccc String, Ddd String, E Character.
A Character, B Character, C Character, D Character, E Character.
```

### *5. Replace the first match in a file with new text*

The following command will replace only the first match of the searching pattern.
``` bash
# The content of test.txt
# B B C D E F
# B C D E F G
# C D E F G H
# C E F G H I

echo sed '1 s/B/A/' test.txt
``` 
**Output:**
```
A B C D E F
B C D E F G
C D E F G H
C E F G H I
```

### *6. Replace the last match in a file with new text*

The following command will replace the last occurrence of the searching pattern.
```bash
sed -e '$s/C/D/' test.txt
```
**Output:**
```
B B C D E F
B C D E F G
C D E F G H
D E F G H I
```

### *7. Replace all files full path with just the filename no directory*
The filename can be retrieved from the file path very easily by using **`basename`** command. `sed` command can also be used to retrieve the filename from the file path. The following command will retrieve the filename only from the file path provided by `echo` command.
``` bash
 echo "/home/ubuntu/temp/myfile.txt" | sed 's/.*\///'
```
**Output:**
```
myfile.txt
```

### *8. Substitute text but only if some other text is found in the string*
Using the following command will replace the scores corresponding to A, B, C and D in the score.txt text with "90~100", "80~90", "70~80" and "0~70" respectively.
``` bash
# The content of score.txt
#A --- Score
#B --- Score
#C --- Score
#D --- Score
sed -e '/A/ s/Score/90~100/; /B/ s/Score/80~90/; /C/ s/Score/70~80/; /D/ s/Score/0~70/;' test.txt
```
**Output:**
```
A --- 90~100
B --- 80~90
C --- 70~80
D --- 0~70
```

### *9. Add string before and after the matching pattern using ‘\\1’*
The sequence of matching patterns of `sed` command is denoted by ‘\1’, ‘\2’ and so on. The following `sed` command will search the pattern, ‘Bash’ and if the pattern matches then it will be accessed by ‘\1′ in the part of replacing text. Here, the text, ‘Bash’ is searched in the input text and, one text is added before and another text is added after ‘\1’.
``` bash
echo "Bash language" | sed  's/\(Bash\)/Learn \1 programming/'
```


**Output:**
```
Learn Bash language programming
```

### *10. Add/Delete by row*
The following is an example of adding/deleting in units of row.
```bash
sed '2,3d' test.txt # Delete the 2~3 row of test.txt
sed '/A/d' test.txt # Delete the line containing the 'A' character in the test.txt file.
sed '4a test' test.txt # Add a new line after line 4, the content is 'test'.
sed '4i test' test.txt # Add a new line before line 4, the content is 'test'.
sed '/test/,+2d' test.txt # Delete matching line and 2 lines after macthing line.
sed 's/[[:blank:]]*$//' test.txt # Using the '[:blank:]' class can be used to remove spaces and tabs from the text or the content of any file.
sed '/^$/d' test.txt # Delete all lines that have only white-space.
sed '/test/!d' # If there is not a match of 'test',delete the line.
sed G test.txt # An empty line is inserted after each line of the file.
```

### *11. If there is a match in line append something to end of line*
The following command will append ’Great’ at the end of the line that contains the text of 'A'.

```bash
#The content of score.txt
#A --- 90~100
#B --- 80~90
#C --- 70~80
#D --- 0~70
sed '/A/ s/$/\tGreat/' score.txt
``` 
**Output:**
```
A --- 90~100    Great
B --- 80~90
C --- 70~80
D --- 0~70
```

### *12. Find case insensitive match and replace with new text*
The following 'sed' command will take the input from the 'echo' command and replace the word, 'bash' by the word, 'C/C++'.
```bash
echo "I like Bash programming" | sed 's/BASH/C\/C++/i'
```
**Output:**
```
I like C/C++ programming
```

### *13. Replace order of two words in a text that match a pattern*
The following `sed` command will take the input of two words from `echo` command and replace the order of these words.

```bash
echo "perl python" | sed -e 's/\([^ ]*\) *\([^ ]*\)/\2 \1/'
```

**Output:**
```
python perl
```
### *14. Execute multiple `sed` commands from the command-line*
‘-e’ option is used in `sed` command to run multiple `sed` scripts from the command line. The following `sed` command will take a text as input from `echo` command and replaces ‘**Ubuntu**‘ by ‘**Kubuntu**‘ and ‘**Centos**‘ by ‘**Fedora**‘.
```bash
echo "Ubuntu Centos Debian" | sed -e 's/Ubuntu/Kubuntu/; s/Centos/Fedora/'
```
**Output:**
```
Kubuntu Fedora Debian
```

### *15. Use ‘&’ to print matched string*
The following command will search the word starting with ‘T’ and replace the text by appending **‘Matched String is –**‘ with the matched word by using ‘&’ symbol. Here, ‘p’ is used to print the modified text.
```bash
echo "Some Testing of sed" | sed -n 's/^T/Matched String is - &/p'
``` 
**Output:**
```
Matched String is - Testing
```

### *16. Capitalize the first character of each word*
```bash
echo "This is a testing of sed!" | sed 's/\([a-z|A-Z]\)\([a-zA-Z0-9]*\)/\u\1\2/g'
``` 
**Output:**
```
This Is A Testing Of Sed!
```

Reference:<br>
[1]. [Linuxhint](https://linuxhint.com/50_sed_command_examples/#s1) <br>
[2]. [The Basics of Using the Sed Stream Editor to Manipulate Text in Linux](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)
