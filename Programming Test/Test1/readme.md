# Linux Assignments Solutions

## Q1: Copy README and Set Permissions

Copy existing file /course/linuxgym/census/README to your home directory and set its permissions:
User/owner: read, write, and execute
Group: read and execute, but not write
Other users: only read
Solution:

```sh
cp /course/linuxgym/census/README ~/
chmod 754 ~/README
```

## Q2: Save Number of Lines In a File

Save the number of lines of file /course/linuxgym/gutenberg/foo.txt into file file_data.txt in your home directory.
Solution:

```Bash
wc -l /course/linuxgym/gutenberg/foo.txt > ~/file_data.txt
```

## Q3: Write a Script That Creates Three Files

Write a script called create.sh that:
Creates two empty files called 00.chk and 01.chk in your home directory.
Creates a file called checklist.txt in your home directory whose content are the filenames of the two files, one per line.
Solution:

```Bash
#!/bin/bash
# create.sh
touch ~/'***'00.chk ~/'***'01.chk
echo "***00.chk" > ~/checklist.txt
echo "***01.chk" >> ~/checklist.txt
```

### Q4: Match Filenames and Save File List

Make a list of all the filenames in directory /course/linuxgym/gutenberg that start with the digit 2, contain at least one character c, and end with 0.txt. Save the list in file file_list.txt in your home directory.
Solution:

```Bash
find /course/linuxgym/gutenberg -type f -name '2*c*0.txt' > ~/file_list.txt
```

## Q5: Write a Script Showing Email Address and Number

Create a script called nemo.sh that outputs your UTS email address and your student number over two separate lines.

Solution:

```Bash
#!/bin/bash
# nemo.sh
echo " email" > ~/student_data.txt
echo " id" >> ~/student_data.txt
cat ~/student_data.txt
```

## Q6: Select Environment Variables

Add code to the given script show_env.sh to save all the lines of your environment that contain at least one character that is not a digit, a lowercase letter, an uppercase letter, 4, _, or = in a file called env1.txt in your current directory.

Solution:

```Bash
#!/bin/bash
# show_env.sh
printenv | grep '[^a-zA-Z0-9_=:]' > env1.txt
printenv | grep ':' >> env2.txt
```

## Q7: Write a Script that Multiplies and Adds

Write a script called mul_add.sh that takes four command line arguments that have to be integer numbers. The script must multiply the first and second arguments, multiply the third and fourth arguments, and add up the two products into a final sum.

Solution:

```Bash
#!/bin/bash
# mul_add.sh
sum=$(( $1 * $2 + $3 * $4 ))
echo $sum
```

## Q8: Grep For Character $ In File

Use command grep to list all the lines in the file /course/linuxgym/gutenberg/7wdvn10.txt that contain at least one $ character. Save the matched lines in a file called grep_data.txt in your home directory.

Solution:

```Bash
grep '\$' /course/linuxgym/gutenberg/7wdvn10.txt > ~/grep_data.txt
```

## Q9: Regular Expression with Alternative

Use command grep -E to list all the lines in the file /course/linuxgym/gutenberg/2mwsm10.txt that contain a match with string "M." or at least one digit. Save the output to your home directory in the file hits.txt.

Solution:

```Bash
grep -E 'M\. | [0-9]' /course/linuxgym/gutenberg/2mwsm10.txt > ~/hits.txt
```

## Q10: Script With Loop Over Arguments

Add code to the given script to assign the list of all arguments passed to the script to the LOOP_OVER variable and test if each argument is an executable file. If so, print its name over one line.

Solution:

```Bash
#!/bin/bash
# edit_loop_code.sh
LOOP_OVER=$@
echo "Will Loop Over $LOOP_OVER"
for ITEM in $LOOP_OVER; do
  if [ -x "$ITEM" ]; then
    echo "$ITEM"
  fi
done
```