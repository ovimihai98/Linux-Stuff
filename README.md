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
  - -q = quit
  - -enter = show next line
  - -pace = show next screen
  - -/string = searches forward for a string (? searches backwards)

tail file => shows the last 10 lines of a file (head shows the first 10)
tail -n 25 file => show the last 25 lines of a file (or head to show first 25)
tail -f file => shows the last 10 lines in real-time
watch -n 3 => runs repeatedly a command with refresh of 3 seconds

## Important Commands

These commands are most used when working with files and drectories

mkdir dir => creates a driectory called dir
 - -p dir1/dir2/dir3 => creates a directory and its parents

 cp file1 file2 => copying file1 to file2 in current directory (if given a path instead of name it will copy to another directory)
 - -i => copy a file and propts the user if it overwrites the destination
 - -p => preserving the file permissions, group and ownership
 - -v => verbose
 - -r dir1 dir2/ => recursively copying dir1 to dir2 in the current directory

mv file1 file2 => renaming file1 to file2
- -i => prompts the user if it overwrites the destination file
- -n => preventing an existing file from bein overwritten
mv file1 dir1/file2 => moving fiel1 to dir1 as file2

rm file1 => removes a file
- -r dir1/ => removes a directory
- -v => verbose
- -rf dir1/ => removes a direcory without prompting
- ri => prompts the user for confirmation

which command => show the command path

## Piping and Command Redirection

Using piping we can connect two or more commands at a time.
Piping sends the ouptut from a command to the input of another command

ls -l /etc/ | head => the output of ls commands which lists the /etc/ directory is piped to head which will show the first 10 files.
ps -ef | grep sshd => checking if sshd process is running


Command redirection

px aux > running.txt => will redirect the output of command ps aux to a text file
ps aux >> running.txt => will redirect the output of command ps aux and appends it to a text file

the > command will redirect the output
the 2> command will redirect the error of the command.
In the same line of command you can redirect both the output and the error:

tail -n 10 /var/log/*.log > output.txt 2>errors.txt


## The grep command

It searches for text patterns

Options:
- -n => print line number
- -i => case insensitive
- -v => inverse the match
- -w => search for whole words
- -a => search in binary files
- -R => search in directory recursively
- -c => display only the no. of matches
- -C n => display a context (n lines before and after the match)


## Compressing and Archiving Files and Directories

Archiving = group together a number of files, the size of the resulting file is the sum of all other files
Compressing = compressing a file and make the file size smaller

tar - Archives a file

Options:
- -c => creates an archive
- -x => extracts the archive
- -t => displays the table of contents of the archive
- -v => verbose
- -z => tells tar to also compress the archvie using GZIP compression
- -f => allows to specify the name of the archive: it is mandatory to write the name of the file after this option
- -j => uses BZIP compression instead of GZIP
- --exclude file => excludes the specified file from the archive

## Hardlinks and Symlinks

ln originalFile HardLink"file" => creates a hardlink for original file pointing to the inode of the data the original file pointed to
ln -l originalFile Symlinkfile => creates a symlink whitch is pointing to the originalFile.

## Account management

Important files for account management:
/etc/passwd => users and informations about users
/etc/shadow => users passwords
/etc/group => groups


Creating an user

useradd [OPTIONS] username

Options:
- -m => creates home directory
- -d [directory name] => specify another home directory
- -c "comment"
- -s shell
- -G => specify the SECONDARY groups (must exist)
- -g => specify the PRIMARY group (must exist)

Ex: useradd -m -d /home/ovidiu -c "Devops Engineer" -s /bin/bash -G sudo,admins,mail ovidiu

usermod [same options as useradd] username => changes an users account

userdel username => deletes an user account [-r removes the home directory as well]

groupadd group_name => creates a group
groupdell group_name => deletes a group

 Monitoring users

 who -H => displays the logged in users
 id => displays the current user and its groups
 whoami => displays EUID

 ## File permissions

Legend:
  u = User
  g = Group
  o = Others/World
  a = all
  
  r = Read
  w = write
  x = execute
  '-' = no access

ls -l or stat [filename] displays permissions to the file

changing permissions:

chmod u+r filename
chmod ug+rwx filename
chmod a+r filename
chmod g-x filename

can be made binrary as well

chmod --reference=file1 file2 => sets the permissions as of a reference file

SUID = SetUserID
SGID = SetGroupID
Sticky Bit

When an executable file with SUID is executed then the resulting process will have the permissions of the owner of the command, not the permissions of the user who executes the command

chmod 4755 /usr/bin/cat => attaches SUID bit on the cat command
chmod u+x /usr/bin/cat => same command

for SGID (mailny used for directories)

chmod 2xxx /dir => attaches SGID bit on the directory
chmod g+s /dir => same command

Sticky bit

chmod 1xxx /dir
chmod o+t /dir

chown new_owner:new_group file => changes the owner and the group owner of the file (can be done separately)

lsattr filename => displaying the file attributes

chattr +-attribute filename => changing the file attributes


## Linux Process Management


process viewing

type command => check if the command is shell built-in or executable file

ps => displaying all processes started in the current terminal
Options:
- -ef => displaying all running processes in the system
- aux => same
- f -u username => displaying all processes of a specific user

pgrep -l sshd => checking if a process called sshd is running

top - shows dynamically the running processes
htop - better version of top

Killing processes:

kill -l => list of all singnals

kill pid => sending SIGTERM (default) to a process by pid

kill -SIGNAL pid1 pid2... => sending a signal to more processes

kill -1 pid => sends a specific signal to a process by pid

pkill process_name => sends a signal to process by name

jobs => shows running jobs

nohup command => starts a prcoess immune to SIGHUP

## Networkig

Getting information about the network interfaces

ifconfig => displays info about the enabled interfaces

ifconfig -a or ip address show => displays info about all interfaces

ifconfig enp0s3 or ip addr show dev enp0s3 => displays info about a specific interface
s
ip -4 address => showing only IPv4 addresses (6 for IPv6)

ip link show => displays L2 info (including MAC address)

ip route show => displays the default gateway

resolvectl status => displaying the DNS servers

ip link set enp0s3 down/up => disabling/enabling interface

Ping command

Sends ICMP packets to the requested IP address
Can do Reverse DNS resolution asking DNS server what is the domain of the IP.

ping [IP address/ FQDN] => sends ping packets to the requested IP address

ping -c 5 [IP address] => sends 5 packets only 

By default Ping waits one second between sending packets, changed using -i option

