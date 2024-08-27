# Linux-Stuff


## Purpose

I have created this repo as a notebook for Linux commands. I have recently switched from Windows to Linux and I taught it might be useful to save the main bash commands somewhere.
I also might add some git commands, vim commands and some commands specific to certain distros such as Debian or Arch, depending on what I feel like testing/installing.

## Keyboard Shortcuts in terminal

CTRL + L => cleares the terminal, same as `clear` command

CTRL + D => closes the shell

CTRL + U => removes the current line

CTRL + A => moves the cursor at the start of the line

CTRL + E => moves the cursor at the end of the line

CTRL + C => stops the current command

CTRL + R => reverse searching into history

## Getting Help

`man` [command] => displays a Man page of the command you set as argumment
Ex: man ls

Shortcuts in man:
  - h => getting help
  - q => quit
  - enter => show next line
  - space => show next screen
  - /[string] => searches forward for the specific string
  - ?[string] => searches backwards for the specific string
  - n/N => next/previous apperance

## Bash History

`history` => shows history of the bash commands

`history` -d [num] => removes the [num] line from the history

`history` -c => removes the entire history

!! => rerunning the last command

![num] => running a specific command from history

!-[num] => running the last numth command from history

##Getting Root access

sudo [command] => runs the specific command as root

sudo passswd root => setting password to root user

passwd [user] => setting password to a specific user

sudo su => becoming temporary root in the terminal

## Paths

. => the current working directory

.. => the parent directory

~ => home directory

cd => change directory

cd ~ => change to home directory

cd - => changing to the last directory

cd /path_to_directory => changes to the path_to_directory

pwd => prints working direcotry

tree => app to better see the directory structure (sudo apt install tree)
-  tree -d . => prints only directories
-  tree -f . => prints absolute paths

## The ls Command

ls /path => lists the contents of the specified path
ls without arguments lists the contents of the current directory
ls can list multiple directories if provided multiple arguments

### Options for ls command
- -l => long listing
- -a => listing all files and directories including hidden ones (.name_of_file is example of a hidden file)
- -1 => listing on a single column
- -d => displaying information about the directory, not about its contents
- -h => displaying the size in human readable format
- -S => displaying sorting by size
- -X => sorting by extension
- --hide=[file_name] => hiding [file_name]
- -R => displaying a directory recursively
- -i => displaying the inode number
- -lu => displaying atime
- -lt => displaying mtime
- -lc => displaying ctime


## File Types and Timestamps

stat file.txt => displays all timestamps of the file
touch file.txt => creates an empty file if it does not exist, update the timestamps if the file exists
touch -a file.txt => changes only the access time to current time
date => displaying the date and time
cal => showing this month's calendar
  - 2024 => calendar of the year 2024
  - 7 2023 => calendar of a specific month in the year
  - -3 show the calendar of the previous, current and next month
date --set="date" setting the date and time


## View Files

Different modes of viewing files in terminal:

cat file => displays the content of a file
cat file1 file2 => displays the content of both files
cat file1 file2 > file3 => concatenates the contents of file1 and file2 into file3

less file => view a file using less (used for big files)
shortcuts for less:
  - q = quit
  - enter = show next line
  - space = show next screen
  - /string = searches forward for a string (? searches backwards)

tail file => shows the last 10 lines of a file (head shows the first 10)
tail -n 25 file => show the last 25 lines of a file (or head to show first 25)
tail -f file => shows the last 10 lines in real-time
watch -n 3 => runs repeatedly a command with refresh of 3 seconds

