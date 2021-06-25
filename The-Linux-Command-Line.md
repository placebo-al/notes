# The Linux Command Line

</br>

## Chapter 1. Navigation

pwd — Print name of current working directory.  
cd — Change directory.

| Shortcut | Result |
|---|---|
| cd | Changes the working directory to your home directory. |
| cd - | Changes the working directory to the previous working directory. |
| cd ˜username | Changes the working directory to the home directory of username. For example, cd ˜bob changes the directory to the home directory of user bob.” |

</br>

## Chapter 2. Exploring the Filesystem

ls — List directory contents.

| Option | Long Option | Description |
|---|---|---|
| -a | --all | List all files, even those with names that begin with a period, which are normally not listed (i.e. hidden). |
| -d | --directory | Ordinarily, if a directory is specified, ls will list the contents of the directory, not the directory itself. Use this option in conjunction with the -l option to see details about the directory rather than its contents. |
| -F | --classify | This option will append an indicator character to the end of each listed name (for example, a forward slash if the name is a directory). |
| -h | --human-readable | In long format listings, display file sizes in human-readable format rather than in bytes. |
| -l |  	 | Display results in long format. |
| -r | --reverse | Display the results in reverse order. Normally, ls displays its results in ascending alphabetical order. |
| -S |  	 | Sort results by file size. |
| -t |  	 | Sort by modification time.” |

file—Determine file type.  
less—View file contents.

| Command | Action |
|---|:---:|
| page up or b | Scroll back one page. |
| page down or Spacebar | Scroll forward one page. |
| Up Arrow | Scroll up one line. |
| Down Arrow | Scroll down one line. |
| G | Move to the end of the text file. |
| 1G or g | Move to the beginning of the text file. |
| /characters | Search forward to the next occurrence of characters. |
| n | Search for the next occurrence of the previous search. |
| h | Display help screen. |
| q | Quit less. |

</br>

## Chapter 3. Directories

| Directory | Comments |
|:---|:---|
| / | The root directory, where everything begins. |
| /bin | Contains binaries (programs) that must be present for the system to boot and run. |
| /boot | Contains the Linux kernel, initial RAM disk image (for drivers needed at boot time), and the boot loader. |

| Interesting files: |  |
|---|---|
| /boot/grub/grub.conf or menu.lst | which are used to configure the boot loader
| /boot/vmlinuz | the Linux kernel |
| /dev | This is a special directory that contains device nodes. “Everything is a file” also applies to devices. Here is where the kernel maintains a list of all the devices it understands. |
| /etc | The /etc directory contains all of the system-wide configuration files. It also contains a collection of shell scripts that start each of the system services at boot time. Everything in this directory should be readable text. |


| /etc | While everything in /etc is interesting, here are some of my all-time favorites: |
|---|---|
| /etc/crontab | a file that defines when automated jobs will run |
| /etc/fstab | a table of storage devices and their associated mount points |
| /etc/passwd | a list of the user accounts |
| /home | In normal configurations, each user is given a directory in /home. Ordinary users can write files only in their home directories. This limitation protects the system from errant user activity. |
| /lib | Contains shared library files used by the core system programs. |
| lost+found | Each formatted partition or device using a Linux filesystem, such as ext3, will have this directory. It is used in the case of a partial recovery from a filesystem corruption event. Unless something really bad has happened to your system, this directory will remain empty. |
| /media | On modern Linux systems the /media directory will contain the mount points for removable media such as USB drives, CD-ROMs, etc. that are mounted automatically at insertion. |
| /mnt | On older Linux systems, the /mnt directory contains mount points for removable devices that have been mounted manually. |
| /opt | The /opt directory is used to install “optional” software. This is mainly used to hold commercial software products that may be installed on your system. |
| /proc | The /proc directory is special. It’s not a real filesystem in the sense of files stored on your hard drive. Rather, it is a virtual filesystem maintained by the Linux kernel. The “files” it contains are peepholes into the kernel itself. The files are readable and will give you a picture of how the kernel sees your computer. |
| /root | This is the home directory for the root account. |
| /sbin | This directory contains “system” binaries. These are programs[…] |
| /usr | The /usr directory tree is likely the largest one on a Linux system. It contains all the programs and support files used by regular users. |
| /usr/bin | /usr/bin contains the executable programs installed by your Linux distribution. It is not uncommon for this directory to hold thousands of programs. |
| /usr/lib | The shared libraries for the programs in /usr/bin. |
| /usr/local | The /usr/local tree is where programs that are not included with your distribution but are intended for system-wide use are installed. Programs compiled from source code are normally installed in /usr/local/bin. On a newly installed Linux system, this tree exists, but it will be empty until the system administrator puts something in it. |
| /usr/sbin | Contains more system administration programs. |
| /usr/share | /usr/share contains all the shared data used by programs in /usr/bin. This includes things like default configuration files, icons, screen backgrounds, sound files, etc.
| /usr/share/doc | Most packages installed on the system will include some kind of documentation. In /usr/share/doc, we will find documentation files organized by package. |
| /var | With the exception of /tmp and /home, the directories we have looked at so far[…] |
| /var/log | /var/log contains log files, records of various system activity. These are very important and should be monitored from time to time. The most useful one is /var/ log/messages. Note that for security reasons on some systems, you must be the superuser to view log files. |

</br>

## Chapter 4. Manipulating files and directories

### Wildcards

| Wildcards | Matches |
|---|---|
| * | Any characters |
| ? | Any single character |
| [characters] | Any character that is a member of the set characters |
| [!characters] | Any character that is not a member of the set characters |
| [[:class:]] | Any character that is a member of the specified class |

### Commonly Used Character Classes

| Character Class | Matches |
|---|---|
| [:alnum:] | Any alphanumeric character |
| [:alpha:] | Any alphabetic character |
| [:digit:] | Any numeral |
| [:lower:] | Any lowercase letter |
| [:upper:] | Any uppercase letter |


cp—Copy files and directories.

| Option |  | Meaning |
|---|---|---|
| -a | --archive | Copy the files and directories and all of their attributes, including ownerships and permissions. Normally, copies take on the default attributes of the user performing the copy. |
| -i | --interactive | Before overwriting an existing file, prompt the user for confirmation. If this option is not specified, cp will silently overwrite files. |
| -r | --recursive | Recursively copy directories and their contents. This option (or the -a option) is required when copying directories. |
| -u | --update | When copying files from one directory to another, copy only files that either don’t exist or are newer than the existing corresponding files in the destination directory. |
| -v | --verbose | Display informative messages as the copy is performed. |

mv—Move/rename files and directories.

| Option | | Meaning |
|----|---|---|
| -i | --interactive | Before overwriting an existing file, prompt the user for confirmation. If this option is not specified, mv will silently overwrite files. |
| -u |  --update | When moving files from one directory to another, move only files that either don’t exist in the destination directory or are newer than the existing corresponding files in the destination directory. |
| -v | --verbose | Display informative messages as the move is performed. |

mkdir—Create directories.  
rm—Remove files and directories.

| Option | | Meaning |
|---|---|---|
| -i | --interactive | Before deleting an existing file, prompt the user for confirmation. If this option is not specified, rm will silently delete files. |
| -r | --recursive | Recursively delete directories. This means that if a directory being deleted has subdirectories, delete them too. To delete a directory, this option must be specified. |
| -f |  --force | Ignore nonexistent files and do not prompt. This overrides the --interactive option. |
| -v | --verbose | Display informative messages as the deletion is performed. |

ln—Create hard and symbolic links.
-s, create a soft link

</br>

## Chapter 5. Working with Commands

type — Indicate how a command name is interpreted.  
which — Display which executable program will be executed.  
man — Display a command’s manual page.  

### Man Page Organization
| Section | Contents |
|---|---|
| 1 | User commands |
| 2 | Programming interfaces for kernel system calls |
| 3 | Programming interfaces to the C library |
| 4 | Special files such as device nodes and drivers |
| 5 | File formats |
| 6 | Games and amusements such as screensavers |
| 7 | Miscellaneous |
| 8 | System administration commands |
  

help - Get help for shell builtins.  
apropos — Display a list of appropriate commands.  
info — Display a command’s info entry.  

| Command | Action |
|---|---|
| ? | Display command help. |
| page up or backspace | Display previous page. |
| page down or Spacebar | Display next page. |
| n | Next—Display the next node. |
| p | Previous—Display the previous node. |
| u | Up—Display the parent node of the currently displayed node, usually a menu. |
| enter | Follow the hyperlink at the cursor location. |
| q | Quit. |

whatis — Display a very brief description of a command.  
alias — Create an alias for a command.  
unalias - Remove an alias for a command

</br>

## Chapter 6. Redirection

\> redirect standard input overwriting the file.  
\>> redirect standard input appending to a file.  
2> redirect standard error to a file.  
2>&1 is the old way of redirecting both stdin and stderr.  
ls -l /bin/usr > ls-output.txt 2>&1.  
&> is the new way of redirecting both stdin and stderr.  
/dev/null is the bitbucket.   
| Read from stdin and pass to stdout.  

cat — Concatenate files.  
sort — Sort lines of text.  
uniq — Report or omit repeated lines.  
wc — Print newline, word, and byte counts for each file.  
grep — Print lines matching a pattern.  
head — Output the first part of a file.  
tail — Output the last part of a file.  
tee — Read from standard input and write to standard output and files.  

</br>

## Chapter 7. Seeing the World as the Shell Sees It

echo — Display a line of text.  
$(( expression)) Arithmetic expansion

| Operator | Description |
|---|---|
| + | Addition |
| - | Subtraction |
| * | Multiplication |
| / | Division (But remember, because expansion supports only integer arithmetic, results are integers.) |
| % | Modulo, which simply means remainder |
| ** | Exponentiation |

`echo Number{1..5}` -Brace Expansion.  
e.g. Number1, Number2, Number3, Number4, Number5

Command substitution allows us to use the output of a command as an expansion:  
`file $(ls /usr/bin/* | grep zip)`

### Quoting
Double quotes, all the special characters used by the shell lose their special meaning and are treated as ordinary characters.  
The exceptions are  

*	$ Dollar sign     
*	\ Backslash  
*	` Back tick  
*	' Single Quote   

If we need to suppress all expansions, we use single quotes.

Backslash Escape Sequences

| Escape Sequence | Meaning |
|---|---|
| \a | Bell (“alert”—causes the computer to beep) |
| \b | Backspace |
| \n | Newline (on Unix-like systems, this produces a linefeed) |
| \r | Carriage return |
| \t | Tab |

</br>

## Chapter 8. Advanced Keyboard Tricks

clear — Clear the screen.  
history — Display the contents of the history list.

Cursor Movement Commands

| Key | Action |
|--------|---|
| ctrl-A | Move cursor to the beginning of the line. |
| ctrl-E | Move cursor to the end of the line. |
| ctrl-F | Move cursor forward one character; same as the right arrow key. |
| ctrl-B | Move cursor backward one character; same as the left arrow key. |
| alt-F | Move cursor forward one word. |
| alt-B | Move cursor backward one word. |
| ctrl-L | Clear the screen and move the cursor to the top left corner. The clear command does the same thing. |


### Text Editing Commands

| Key | Action |
|--------|---|
| ctrl-D | Delete the character at the cursor location. |
| ctrl-T | Transpose (exchange) the character at the cursor location with the one preceding it. |
| alt-T | Transpose the word at the cursor location with the one preceding it. |
| alt-L | Convert the characters from the cursor location to the end of the word to lowercase. |
| alt-U | Convert the characters from the cursor location to the end of the word to uppercase. |

Cut and Paste Commands. 

| Key | Action |
|:--------:|---|
| ctrl-K | Kill text from the cursor location to the end of line. |
| ctrl-U | Kill text from the cursor location to the beginning of the line. |
| alt-D | Kill text from the cursor location to the end of the current word. |
| alt-backspace | Kill text from the cursor location to the beginning of the current word. If the cursor is at the beginning of a word, kill the previous word. |
| ctrl-Y | Yank text from the kill-ring and insert it at the cursor location. |

History Commands

| Key | Action |
|--------|---|
| ctrl-P | Move to the previous history entry. Same action as the up arrow. |
| ctrl-N | Move to the next history entry. Same action as the down arrow. |
| alt-< | Move to the beginning (top) of the history list. |
| alt-> | Move to the end (bottom) of the history list; i.e., the current command line. |
| ctrl-R | Reverse incremental search. Searches incrementally from the current command line up the history list. |
| alt-P | Reverse search, non-incremental. With this key, type the search string and press enter before the search is performed. |
| alt-N | Forward search, non-incremental. |
| ctrl-O | Execute the current item in the history list and advance to the next one. This is handy if you are trying to re-execute a sequence of commands in the history list. |

ctrl-R: starts a reverse search of bash history.  
ctrl-J: to copy the line to the current command. 

History Expansion Commands. 

| Sequence | Action |
|:---:|---|
| !! | Repeat the last command. It is probably easier press the up arrow and enter. |
| ! number | Repeat history list item number. |
| ! string | Repeat last history list item starting with string. |
| !? string | Repeat last history list item containing string. |

script - which can be used to record an entire shell session and store it in a file.  
The basic syntax of the command is  
> script [file]

</br>

## Chapter 9. Permissions

File Types

| Attribute | File Type |
|:---:|---|
| - | A regular file. |
| d | A directory. |
| l | A symbolic link. Notice that with symbolic links, the remaining file attributes are always rwxrwxrwx and are dummy values. The real file attributes are those of the file the symbolic link points to. |
| c | A character special file. This file type refers to a device that handles data as a stream of bytes, such as a terminal or modem. |
| b | A block special file. This file type refers to a device that handles data in blocks, such as a hard drive or CD-ROM drive. |

Permission attributes.  
|Attribute| Files | Directories |
|---|---|---|
| r | Allows a file to be opened and read. | Allows a directory’s contents to be listed if the execute attribute is also set. |
| w | Allows a file to be written to or truncated; however, this attribute does not allow files to be renamed or deleted. The ability to delete or rename files is determined by directory attributes. | Allows files within a directory to be created, deleted, and renamed if the execute attribute is also set. |
| x | Allows a file to be treated as a program and executed. Program files written in scripting languages must also be set as readable to be executed. | Allows a directory to be entered; e.g., cd directory. |

File Modes in Binary and Octal
| Octal | Binary | File Mode |
|---|---|---|
| 0 | 000 | --- |
| 1 | 001 | --x |
| 2  | 010 | -w- |
| 3  | 011 | -wx |
| 4  | 100 | r-- |
| 5  | 101 | r-x |
| 6  | 110 | rw- |
| 7  | 111 | rwx |

chmod Symbolic Notation

| Symbol | Meaning |
|---|---|
| u | Short for user but means the file or directory owner. |
| g | Group owner. |
| o | Short for others but means world. |
| a | Short for all; the combination of u, g, and o. |

id — Display user identity.  
chmod — Change a file’s mode.  
umask — Set the default file permissions.  
su — Run a shell as another user.  
sudo — Execute a command as another user.  
chown — Change a file’s owner.  

### chown Argument Examples

| Argument | Results |
|---|---|
| bob | Changes the ownership of the file from its current owner to user bob. |
| bob:users | Changes the ownership of the file from its current owner to user bob and changes the file group owner to group users. |
| :admins | Changes the group owner to the group admins. The file owner is unchanged. |
| bob: | Change the file owner from the current owner to user bob and changes the group owner to the login group of user bob. |

chgrp — Change a file’s group ownership.  
passwd — Change a user’s password.  

</br>

## Chapter 10 Processes 

ps — Report a snapshot of current processes.

Process States

| State | Meaning |
|---|---|
| R | Running. The process is running or ready to run. |
| S | Sleeping. The process is not running; rather, it is waiting for an event, such as a keystroke or network packet. |
| D | Uninterruptible sleep. Process is waiting for I/O such as a disk drive. |
| T | Stopped. Process has been instructed to stop (more on this later). |
| Z | A defunct or “zombie” process. This is a child process that has terminated but has not been cleaned up by its parent. |
| < | A high-priority process. It’s possible to grant more importance to a process, giving it more time on the CPU. This property of a process is called niceness. A process with high priority is said to be less nice because it’s taking more of the CPU’s time, which leaves less for everybody else. |
| N | A low-priority process. A process with low priority (a nice process) will get processor time only after other processes with higher priority have been serviced. |

### BSD style ps Column Headers

| Header | Meaning |
|---|---|
| USER | User ID. This is the owner of the process. |
| %CPU | CPU usage as a percent. |
| %MEM | Memory usage as a percent. |
| VSZ | Virtual memory size. |
| RSS | Resident Set Size. The amount of physical memory (RAM) the process is using in kilobytes. |
| START | Time when the process started. For values over 24 hours, a date is used. |

top — Display tasks.

### top Information Fields
|Row | Field | Meaning |
---|---|---|
| 1 | top | Name of the program. |
|  	| 14:59:20 | Current time of day. |
|  	| up 6:30 | This is called uptime. It is the amount of time since the machine was last booted. In this example, the system has been up for 6½ hours. |
|  	| 2 users | Two users are logged in. |
|  	| load average: | Load average refers to the number of processes that are waiting to run; that is, the number of processes that are in a runnable state and are sharing the CPU. Three values are shown, each for a different period of time. The first is the average for the last 60 seconds, the next the previous 5 minutes, and finally the previous 15 minutes. Values under 1.0 indicate that the machine is not busy. |
| 2 | Tasks: | This summarizes the number of processes and their various process states. |
|  	| 0.7%us | 0.7% of the CPU is being used for user processes. This means processes outside of the kernel itself. |
|  	| 1.0%sy | 1.0% of the CPU is being used for system (kernel) processes. |
|  	| 0.0%ni | 0.0% of the CPU is being used by nice (low-priority) processes. |
|  	| 98.3%id | 98.3% of the CPU is idle[…] |

jobs — List active jobs.  
ctrl-C to interrupts a program.  
& - After the process starts in the background.  
ctrl-Z stops a process.  
bg — Place a job in the background. %1 jobspec.  
fg — Place a job in the foreground. %1 jobspec.  
kill — Send a signal to a process.  

Common Signals  
| Number | Name | Meaning|
|---|---|---|
| 1 | HUP | Hang up. This is a vestige of the good old days when terminals were attached to remote computers with phone lines and modems. The signal is used to indicate to programs that the controlling terminal has “hung up.” The effect of this signal can be demonstrated by closing a terminal session. The foreground program running on the terminal will be sent the signal and will terminate.   This signal is also used by many daemon programs to cause a reinitialization. This means that when a daemon is sent this signal, it will restart and reread its configuration file. The Apache web server is an example of a daemon that uses the HUP signal in this way.
| 2 | INT | Interrupt. Performs the same function as the ctrl-C key sent from the terminal. It will usually terminate a program.  
| 9 | KILL | Kill. This signal is special. Whereas programs may choose to handle signals sent to them in different ways, including by ignoring them altogether, the KILL signal is never actually sent to the target program. Rather, the kernel immediately terminates the process. When a process is terminated in this manner, it is given no opportunity to “clean up” after itself or save its work. For this reason, the KILL signal should be used only as a last resort when other termination signals fail.
| 15 | TERM | Terminate. This is the default signal sent by the kill command. If a program is still “alive” enough to receive signals, it will terminate.
| 18 | CONT | Continue. This will restore a process after a STOP signal.
| 19 | STOP | Stop. This signal causes a process to pause without terminating. Like the KILL signal, it is not sent to the target process, and thus it cannot be ignored.
| 3 | QUIT | Quit.
| 11 | SEGV | Segmentation violation. This signal is sent if a program makes illegal use of memory; that is, it tried to write somewhere it was not allowed to.
| 20 | TSTP | Terminal stop. This is the signal sent by the terminal when ctrl-Z is pressed. Unlike the STOP signal, the TSTP signal is received by the program but the program may choose to ignore it.
| 28 | WINCH | Window change. This is a signal sent by the system when a window changes size. Some programs, like top and less, will respond to this signal by redrawing themselves to fit the new window dimensions.

killall — Kill processes by name.  
shutdown — Shut down or reboot the system.

### Other Process-Related Commands

| Command | Description |
|---|---|
| pstree | Outputs a process list arranged in a tree-like pattern showing the parent/child  |relationships between processes.
| vmstat | Outputs a snapshot of system resource usage including memory, swap, and disk I/O. To  |see a continuous display, follow the command with a time delay (in seconds) for updates (e.g., vmstat 5). Terminate the output with ctrl-C.
| xload | A graphical program that draws a graph showing system load over time. |
| tload | Similar to the xload program, but draws the graph in the terminal. Terminate the  |output with ctrl-C.

</br>

## Chapter 11. The Environment

### Environment Variables

| Variable | Contents |
|---|---|
| DISPLAY | The name of your display if you are running a graphical environment. Usually this is :0, meaning the first display generated by the X server. |
| EDITOR | The name of the program to be used for text editing. |
| SHELL | The name of your shell program. |
| HOME | The pathname of your home directory. |
| LANG | Defines the character set and collation order of your language. |
| OLD_PWD | The previous working directory. |
| PAGER | The name of the program to be used for paging output. This is often set to /usr/bin/less. |
| PATH | A colon-separated list of directories that are searched when you enter the name of an executable program. |
| PS1 | Prompt String 1. This defines the contents of your shell prompt. As we will later see, this can be extensively customized. |
| PWD | The current working directory. |
| TERM | The name of your terminal type. Unix-like systems support many terminal protocols; this variable sets the protocol to be used with your terminal emulator. |
| TZ | Specifies your time zone. Most Unix-like systems maintain the computer’s internal clock in Coordinated Universal Time (UTC) and then display the local time by applying an offset specified by this variable. |
| USER | Your username. |


### Startup Files for Login Shell Sessions

| File | Contents |
|---|---|
| /etc/profile | A global configuration script that applies to all users. |
| ~/.bash_profile | A user’s personal startup file. Can be used to extend or override settings in the global configuration script. |
| ~/.bash_login | If ~/.bash_profile is not found, bash attempts to read this script. |
| ~/.profile | If neither ~/.bash_profile nor ~/.bash_login is found, bash attempts to read this file. This is the default in Debian-based distributions, such as Ubuntu. |

### Startup Files for Non-Login Shell Sessions

| File | Contents |
|---|---|
| /etc/bash.bashrc | A global configuration script that applies to all users. |
| ~/.bashrc | A user’s personal startup file. Can be used to extend or override settings in the global configuration script. |


printenv — Print part or all of the environment.  
set — Set shell options.  
export — Export environment to subsequently executed programs.  
alias — Create an alias for a command.  


### Additions to Our .bashrc File
| Line | Meaning |
|---|---|
| Umask 0002 | Sets the umask to solve the problem with shared directories we discussed in Chapter 9. |
| export HISTCONTROL=ignoredups | Causes the shell’s history recording feature to ignore a command if the same command was just recorded. |
| export HISTSIZE=1000 | Increases the size of the command history from the default of 500 lines to 1000 lines. |
| alias l.='ls -d .* --color=auto' | Creates a new command called l., which displays all directory entries that begin with a dot. |
| alias ll='ls -l –color=auto' | Creates a new command called ll, which displays a long-format directory listing. |

</br>

## Chapter 13 Customising the Prompt

Escape Codes Used in Shell Prompts

| Sequence | Value Displayed |
|---|---|
| \a | ASCII bell. This makes the computer beep when it is encountered. |
| \d | Current date in day, month, date format; for example, “Mon May 26” |
| \h | Hostname of the local machine minus the trailing domain name |
| \H | Full hostname |
| \j | Number of jobs running in the current shell session |
| \l | Name of the current terminal device |
| \n | A newline character |
| \r | A carriage return |
| \s | Name of the shell program |
| \t | Current time in 24-hour, hours:minutes:seconds format |
| \T | Current time in 12-hour format |
| \@ | Current time in 12-hour, am/pm format |
| \A | Current time in 24-hour, hours:minutes format |
| \u | Username of the current user |
| \v | Version number of the shell |
| \V | Version and release numbers of the shell |
| \w | Name of the current working directory |
| \W | Last part of the current working directory name |
| \\! | History number of the current command |
| \\# | Number of commands entered during this shell session |
| \\$ | This displays a “$” character unless you have superuser privileges. In that case, it displays a “#” instead. |
| \\[ | This signals the start of a series of one or more non-printing characters. It is used to embed non[…] |

</br>

## Chapter 14 Package Management

Packaging System tools
| Distributions | Low-Level Tools | High-Level Tools |
| Debian style | dpkg | apt-get, aptitude |
| Fedora, Red Hat Enterprise Linux, CentOS | rpm | yum |

### Package Search Commands
| Style | Command(s) |
| ---|--- |
| Debian | apt-get update		apt-cache search search_string |
| Red Hat | yum search search_string |

### Package Installation Commands
| Style | Command(s) |
| ---|--- |
| Debian | apt-get update		apt-get install package_name |
| Red Hat | yum install package_name |

### Low-Level Package Installation Commands
| Style | Command |
| ---|--- |
| Debian | dpkg --install package_file |
| Red Hat | rpm -ipackage_file |

### Package Removal Commands
| Style | Command |
| ---|--- |
| Debian | apt-get remove package_name |
| Red Hat | yum erase package_name |

### Package Update Commands
| Style | Command(s) |
| ---|--- |
| Debian | apt-get update; apt-get upgrade |
| Red Hat | yum update |

### Low-Level Package Upgrade Commands
| Style | Command |
| ---|--- |
| Debian | dpkg --install package_file |
| Red Hat | rpm -U package_file |

### Package Listing Commands
| Style | Command |
| ---|--- |
| Debian | dpkg --list |
| Red Hat | rpm -qa |

### Package Status Commands
| Style | Command |
| ---|--- |
| Debian | dpkg --status package_name |
| Red Hat | rpm -q package_name |

### Package Information Commands 
| Style | Command |
| ---|--- |
| Debian | apt-cache show package_name |
| Red Hat | yum info package_name |

### Package File Identification Commands
| Style | Command |
| ---|--- |
| Debian | dpkg --search file_name |
| Red Hat | rpm -qf file_name |

</br>

## Chapter 15 Storage Media

mount — Mount a filesystem.  
>    -t allows you to decide the File System type.  

Mount an image file as though it were a device and attach it to the filesystem tree:  
mkdir /mnt/iso_image   
mount -t iso9660 -o loop image.iso /mnt/iso_image

umount — Unmount a filesystem.  
fdisk — Partition table manipulator.  
| Command | Action |
|---|---|  
| a | toggle a bootable flag |
| b | edit bsd disklabel |
| c | toggle the dos compatibility flag |
| d | delete a partition |
| l | list known partition types |
| m | print this menu |
| n | add a new partition |
| o | create a new empty DOS partition table |
| p | print the partition table |
| q | quit without saving changes |
| s | create a new empty Sun disklabel |
| t | change a partition's system id |
| u | change display/entry units |
| v | verify the partition table |
| w | write table to disk and exit |
| x | extra functionality (experts only) |
Command (m for help):

fsck — Check and repair a filesystem.  
fdformat — Format a floppy disk.  
mkfs — Create a filesystem.  

dd — Write block-oriented data directly to a device.  
> dd if=input_file of=output_file [bs=block_size [count=
blocks]]

genisoimage (mkisofs) — Create an ISO 9660 image file.   
wodim (cdrecord) — Write data to optical storage media.  
md5sum — Calculate an MD5 checksum.  

### /etc/fstab Fields
| Field | Contents | Description |
|---|---|---|
| 1 | Device | Traditionally, this field contains the actual name of a device file associated with the physical device, such as /dev/hda1 (the first partition of the master device on the first IDE channel). But with today’s computers, which have many devices that are hot pluggable (like USB drives), many modern Linux distributions associate a device with a text label instead. This label (which is added to the storage medium when it is formatted) is read by the operating system when the device is attached to the system. That way, no matter which device file is assigned to the actual physical device, it can still be correctly identified. |
| 2 | Mount point | The directory where the device is attached to the filesystem tree |
| 3 | Filesystem type | Linux allows many filesystem types to be mounted. Most native Linux filesystems are ext3, but many others are supported, such as FAT16 (msdos), FAT32 (vfat), NTFS (ntfs), CD-ROM (iso9660), etc. |
| 4 | Options | Filesystems can be mounted with various options. It is possible, for example, to mount filesystems as read only or to prevent any programs from being executed from them (a useful security feature for removable media[…]  

### Linux Storage Device Names.  
| Pattern | Device |
|---|---|
| /dev/fd* | Floppy disk drives |
| /dev/hd* | IDE (PATA) disks on older systems. Typical motherboards contain two IDE connectors, or channels, each with a cable with two attachment points for drives. The first drive on the cable is called the master device and the second is called the slave device. The device names are ordered such that /dev/hda refers to the master device on the first channel, /dev/hdb is the slave device on the first channel; /dev/hdc, the master device on the second channel, and so on. A trailing digit indicates the partition number on the device. For example, /dev/hda1 refers to  |the first partition on the first hard drive on the system while /dev/hda refers to the entire drive.
| /dev/lp* | Printers |
| /dev/sd* | SCSI disks. On recent Linux systems, the kernel treats all disk-like devices (including PATA/SATA hard disks, flash drives, and USB mass storage devices such as portable music players and digital cameras) as SCSI disks. The rest of the naming system is similar to the older /dev/hd* naming scheme described above. |
| /dev/sr* | Optical drives (CD/DVD readers and burners) |
  
  
If you work on a system that does not automatically mount removable devices, start a real-time view of the /var/log/messages file:  
`sudo tail -f /var/log/messages  `
Plug in the removable device, the kernel will notice the device and probe it:  
After the display pauses again, press ctrl-C to get the prompt back.  
With our device name in hand, we can now mount the flash drive:  

</br>

## Chapter 16. Networking

ping — Send an ICMP ECHO_REQUEST to network hosts.  
traceroute — Print the route packets trace to a network host.  
netstat — Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.  
* -r display the routing table  
* -ie same as ifconfig

ftp — Internet file transfer program.

Examples of Interactive ftp Commands

| Command | Meaning |
|---|---|
| ftp fileserver | Invoke the ftp program and have it connect to the FTP server fileserver. |
| anonymous | Login name. After the login prompt, a password prompt will appear. Some servers will accept a blank password. Others will require a password in the form of an email address. In that case, try something like user@example.com. |
| cd pub/cd_images/Ubuntu-8.04 | Change to the directory on the remote system containing the desired file. Note that on most anonymous FTP servers, the files for public downloading are found somewhere under the pub directory. |
| ls | List the directory on the remote system. |
| lcd Desktop | Change the directory on the local system to ˜/Desktop. In the example, the ftp program was invoked when the working directory was ˜. This command changes the working directory to ˜/Desktop. |
| get ubuntu-8.04-desktop-i386.iso | Tell the remote system to transfer the file ubuntu-8.04-desktop-i386.iso to the local system. Since the working directory on the local system was changed to ˜/Desktop, the file will be downloaded there. |
| bye | Log off the remote server and end the ftp program session. The commands quit and exit may also be used. |

lftp — An improved Internet file transfer program.  
wget — Non-interactive network downloader.  
ssh — OpenSSH SSH client (remote login program).  
scp — Secure copy (remote file copy program).  
sftp — Secure file transfer program.  
</br>

## Chapter 17 Searching for Files

locate — Find files by name.  
updatedb - Updates the database used by locate.  
find — Search for files in a directory hierarchy.  

	- find File Types with -type
| File Type | Description |
|---|---|
| b | Block special device file |
| c | Character special device file |
| d | Directory |
| f | Regular file |
| l | Symbolic link |

    - find Size Units -size
| Character | Unit |
|---|---|
| b | 512-byte blocks (the default if no unit is specified) |
| c | Bytes |
| w | 2-byte words |
| k | Kilobytes (units of 1024 bytes) |
| M | Megabytes (units of 1,048,576 bytes) |
| G | Gigabytes (units of 1,073,741,824 bytes) |

	- find Tests
| Test | Description |
|---|---|
| -cmin n | Match files or directories whose content or attributes were last modified exactly n minutes ago. To specify fewer than n minutes ago, use -n; to specify more than n minutes ago, use +n. |
| -cnewer file | Match files or directories whose contents or attributes were last modified more recently than those of file. |
| -ctime n | Match files or directories whose contents or attributes (i.e., permissions) were last modified n * 24 hours ago. |
| -empty | Match empty files and directories. |
| -group name | Match file or directories belonging to group name. name may be expressed as either a group name or as a numeric group ID. |
| -iname pattern | Like the -name test but case insensitive. |
| -inum n | Match files with inode number n. This is helpful for finding all the hard links to a particular inode. |
| -mmin n | Match files or directories whose contents were modified n minutes ago. |
| -mtime n | Match files or directories whose contents only were last modified n * 24 hours ago. |
| -name pattern | Match files and directories with the specified wildcard pattern. |
| -newer file | Match files and directories whose contents were modified more recently than the specified file. This is very useful when writing shell scripts that perform file backups. Each time you make a backup, update a file (such as a log) and then use find to determine which files have changed since the last update. |
| -nouser | Match file and directories that do not belong to a valid user. This can be used to find files belonging to deleted accounts or to detect activity by attackers. |
| -nogroup | Match files and directories that do not belong to a valid group. |
| -perm mode | Match files or directories that have permissions set to the specified mode. mode may be expressed by either octal or symbolic notation. |
| -samefile name | Similar to the -inum test. Matches files that share the same inode number as file name. |
| -size n | Match files of size n. |
| -type c | Match files of type c. |
| -user name | Match files or directories belonging to name. name may be expressed by a username or by a numeric user ID. |

	- find Logical Operators
| Operator | Description |
|---|---|
| -and | Match if the tests on both sides of the operator are true. May be shortened to -a. Note that when no operator is present, -and is implied by default. |
| -or | Match if a test on either side of the operator is true. May be shortened to -o. |
| -not | Match if the test following the operator is false. May be shortened to -!. |
| ( ) | Groups tests and operators together to form larger expressions. This is used to control the precedence of the logical evaluations. By default, find evaluates from left to right. It is often necessary to override the default evaluation order to obtain the desired result. Even if not needed, it is helpful sometimes to include the grouping characters to improve readability of the command. Note that since the parentheses characters have special meaning to the shell, they must be quoted when using them on the command line to allow them to be passed as arguments to find. Usually the backslash character is used to escape them. |

example  
`find ˜ \( -type f -not -perm 0600 \) -or \( -type d -not -perm 0700 \)`

	- find AND/OR Logic
Results of expr1
Operator
expr2 is...
True
-and
Always performed
False
-and
Never performed
True
-or
Never performed
False
-or
Always performed

	- Predefined find Actions

| Action | Description |
|---|---|
| -delete | Delete the currently matching file. |
| -ls | Perform the equivalent of ls -dils on the matching file. Output is sent to standard output. |
| -print | Output the full pathname of the matching file to standard output. This is the default action if no other action is specified. |
| -quit | Quit once a match has been made. |
| -exec command {} ; | Where command is the name of a command, {} is a symbol for the pathname, semicolon indicates the end of the command. |

 ` -exec rm '{}' ';'`  
 ` -ok command {} ;`   
As with exec but the user is prompted before execution of the command

; +  Semicolon allows the exec program to launch on each new instance the plus command executes after the find command completes

If we have spaces in the filenames we can use -print0 to separate with null instead of space.  
example:   
`find ˜ -iname '*.jpg' -print0 | xargs --null ls -l`

xargs — Build and execute command lines from standard input.  
example   using find works the same as using the + ending to see the limit of xargs you can use the --show-limits option.  
` find ˜ -type f -name 'foo*' -print | xargs ls -l `

	- find Options
| Option | Description |
|---|---|
| -depth | Direct find to process a directory’s files before the directory itself. This option is automatically applied when the -delete action is specified. |
| -maxdepth levels | Set the maximum number of levels that find will descend into a directory tree when performing tests and actions. |
| -mindepth levels | Set the minimum number of levels that find will descend into a directory tree before applying tests and actions. |
| -mount | Direct find not to traverse directories that are mounted on other filesystems. |
| -noleaf | Direct find not to optimize its search based on the assumption that it is searching a Unix-like filesystem. This is needed when scanning DOS/Windows filesystems and CD-ROMs. |


touch — Change file times, and creates empty files.  
stat — Display file or filesystem status, use -x on mac for unix output

</br>

## Chapter 18 Archiving and Backup

gzip — Compress or expand files.

gzip Options

| Option | Description |
|---|---|
| -c | Write output to standard output and keep original files. May also be specified with --stdout and --to-stdout. |
| -d | Decompress. This causes gzip to act like gunzip. May also be specified with --decompress or --uncompress. |
| -f | Force compression even if a compressed version of the original file already exists. May also be specified with --force. |
| -h | Display usage information. May also be specified with --help. |
| -l | List compression statistics for each file compressed. May also be specified with --list. |
| -r | If one or more arguments on the command line are directories, recursively compress files contained within them. May also be specified with --recursive. |
| -t | Test the integrity of a compressed file. May also be specified with --test. |
| -v | Display verbose messages while compressing. May also be specified with --verbose. |
| -number | Set amount of compression. number is an integer in the range of 1 (fastest, least compression) to 9 (slowest, most compression). The values 1 and 9 may also be expressed as --fast and --best, respectively. The default value is 6. |

bzip2 — A block sorting file compressor.  
tar — Tape-archiving utility.

tar Modes

| Mode | Description |
|---|---|
| c | Create an archive from a list of files and/or directories. |
| x | Extract an archive. |
| r | Append specified pathnames to the end of an archive. |
| t | List the contents of an archive. |

zip — Package and compress files.  
rsync — Remote file and directory synchronization.
Example
rsync options source destination

Example across a network with remote-sys being the server name
sudo rsync -av --delete --rsh=ssh /etc /home /usr/local remote-sys:/backup

</br>

## Chapter 20 Text Processing

cat—Concatenate files and print on the standard output.  
sort—Sort lines of text files.

Common sort Options 
| Option | Long Option | Description |
|---|---|---|
| -b | --ignore-leading-blanks | By default, sorting is performed on the entire line, starting with the first character in the line. This option causes sort to ignore leading spaces in lines and calculates sorting based on the first non-whitespace character on the line. |
| -f | --ignore-case | Makes sorting case insensitive. |
| -n | --numeric-sort | Performs sorting based on the numeric evaluation of a string. Using this option allows sorting to be performed on numeric values rather than alphabetic values. |
| -r | --reverse | Sort in reverse order. Results are in descending rather than ascending order. |
| -k | --key=field1[,field2] | Sort based on a key field located from field1 to field2 rather than the entire line. |
| -m | --merge | Treat each argument as the name of a presorted file. Merge multiple files into a single sorted result without performing any additional sorting. |
| -o | --output=file | Send sorted output to file rather than to standard output. |
| -t | --field-separator=char | Define the field-separator character. By default, fields are separated by spaces or tabs. |

uniq—Report or omit repeated lines.

Common uniq Options
| Option | Description | 
|---|---|
| -c | Output a list of duplicate lines preceded by the number of times the line occurs. |
| -d | Output only repeated lines, rather than unique lines. |
| -f n | Ignore n leading fields in each line. Fields are separated by whitespace as they are in sort; however, unlike sort, uniq has no option for setting an alternative field separator. |
| -i | Ignore case during the line comparisons. |
| -s n | Skip (ignore) the leading n characters of each line. |
| -u | Output only unique lines. This is the default. |

cut—Remove sections from each line of files.  
paste—Merge lines of files.  
join—Join lines of two files on a common field.  
comm—Compare two sorted files line by line.  
diff—Compare files line by line.  
patch—Apply a diff file to an original.  
tr—Translate or delete characters.  
sed—Stream editor for filtering and transforming text.  
aspell—Interactive spell checker.  


</br>

## ACL Cheat sheet 

| Getting ACLs | Command String |
|---|---|
| Get ACL  | getfacl  file.txt |
| Get Default ACL | getfacl -d  file.txt |
| Get ACL without comment | getfacl -c  file.txt |
| Get ACL in tabular format | getfacl --tabular  file.txt |
| Get ACLs recursively | getfacl -R /home/share |
| Get ACLs and show UID and GID | getfacl --numeric  file.txt |

</br>

| Setting ACLs | Command String |
|---|---|
| Modify ACL | setfacl -m user:bob:rwx  file.txt |
| Modify ACL – short form | setfacl -m u:bob:rwx  file.txt |
| Modify multiple ACLs | setfacl -m user:bob:rwx,user:rob:r  file.txt |
| Modify Group ACL | setfacl -m group:wheel:rwx  file.txt |
| Modify Default ACL on dir | setfacl -d -m group:wheel:rwx  /home/share |
  
</br>

| Removing ACLs | Command String |
|---|---|
| Remove ACL | setfacl -x user:bob,user:rob  file.txt |
| Remove Default ACL | setfacl -k  /home/share |
| Remove all ACLs | setfacl -b  file.txt |

</br>

| Interesting Uses for ACLs | Command String |
|---|---|
| Copy ACL from one file1 to file2 | getfacl file.txt | setfacl --set-file=-  file.bak |
| Save ACL to a config file | getfacl -c file.txt >  shareacls.txt |
| Set ACLs from a config file | setfacl -M shareacls.txt /home/share/* |
| Copy ACL to Default | getfacl /home/share/ | setfacl -d -M- /home/backup/  |
| Revoke write access to all users/groups | setfacl -m m::rx file  |

</br>

| Copy/Preserve ACLs | Command String |
|---|---|
| Copy files with ACLs | cp -p /home/share/file.txt /home/backup/ |
| Archive files with ACLs | tar --acls -czvpf  archive.tar.gz /home/share/ |
| Get ACL Tree and store in file | getfacl -R /home/share/ > Tree.facl |
| Restore ACL Tree | setfacl --restore Tree.facl |

</br>

## Archivers Cheatsheet 

| Task | Options | Example |
|---|---|---|
| Create archive | -c | tar -cf etc.tar /etc |
| Create gzip archive | -z | tar -czf etc.tar.gz /etc |
| Create bzip archive | -j | tar -cjf etc.tar.gz /etc |
| Create xz archive | -J | tar -cJf etc.tar.xz /etc |
| Create archive with permissions | -p | tar -cpf etc.tar. /etc |
| Display verbose output | -v | tar -cvpf etc.tar /etc |
| Display archive | -t | tar -tf etc.tar |
| Display gzip archive  | -tz | tar -tz etc.tar.gz |
| Display bzip2 archive  | -tj | tar -tj etc.tar.bz2 |
| Display xz archive  | -tJ | tar -tJ etc.tar.xz |
| Display verbose output | -v | tar -cvpf etc.tar /etc |
| Extract tar archive | -x | tar -xf archive.tar |
| Extract tar gzip archive | -xz | tar -xzf archive.tar.gz |
| Extract tar bzip2 archive | -xj | tar -xjf archive.tar.bz2 |
| Extract xz archive | -xJ | tar xJf archive.tar.xz |
| Extract to new location | -C | tar -xf archive.tar -C /home/bob/ |
| Extract with permissions | -p | tar -xpf archive.tar  |
| Create full backup with incremental file | -g | tar -czvg snapshotfile -f full.tar.gz /home |
| Create incremental backup | -g | tar -czvg snapshotfile -f monday.tar.gz /home |

</br>

## Compressor tools 

| Task | Example     |
|---|---|
| Create gzip archive | gzip file |
| Create bzip2 archive | bzip2 -z file |
| Create zip archive | zip archive file    |
| Create xz archive | xz file |
| Extract gzip archive | gunzip file.gz |
| Extract bzip2 archive | bunzip2 file.bz2 |
| Extract zip archive | unzip file.zip |
| Extract xz archive | unxz file.xz |

</br>

## Cheatsheet - Pattern and String Substitution 


### String Operations

| ${varname#pattern}  | Remove up to the FIRST occurrence of the match from the beginning of the line  |
|---|---|
| ${varname##pattern}  | Remove up to the LAST occurrence of the match from the beginning of the line  |
| ${varname%pattern}  | Remove the FIRST occurrence of the match starting from the end of the line  |
| ${varname%%pattern}  | Remove the LAST occurrence of the match starting from the end of the line  |
| ${varname/pattern/string}  | Replace matching pattern with string  |
| ${varname/#pattern/string}  | Replace matching pattern at the BEGINNING of the line with string  |
| ${varname/%pattern/string}  | Replace matching pattern at the END of the line with string  |
| ${varname//pattern/string}  | Replace ALL matching occurrences of pattern with string  |
| ${varname:offset:length}  | Returns the substring of $varname starting at offset and up to the length of characters  |
| ${varname: -length}  | Returns the substring of $varname starting at offset from the END  |

</br>

### Variable Manipulations 
| ${#varname}  | Get length of variable  |
|---|---|
| ${!pattern*}  | Indirect reference. Matches all variables names that match the pattern  |
| ${varname^}  | Transform first character of string to uppercase  |
| ${varname^^}  | Transform all characters of string to uppercase  |
| ${varname,}  | Transform first character of string to lowercase  |
| ${varname,,}  | Transform all characters of string to lowercase  |

</br>

### Expansions to handle empty variables
| ${varname:-$var}  | If $varname isn't null return it's value, else return $var  |
|---|---|
| ${varname:=$var}  | If $varname isn't null return it's value, else assign it to $var and return it's value  |
| ${varname:?$var}  | If $varname isn't null return it's value, otherwise print varname: $var and abort   |
| ${varname:+$var}  | If $varname isn't null, return $var, otherwise return null  |
   
</br>

### String Operations Examples
VAR="The quick brown fox jumped over the fox"
| ${VAR#*fox}  | jumped over the fox  |
|---|---|
| ${VAR%fox*}  | The quick brown fox jumped over the  |
| ${VAR%%fox*}  | The quick brown  |
| ${VAR/fox/dog}  | The quick brown dog jumped over the fox  |
| ${VAR//fox/dog}  | The quick brown dog jumped over the dog  |
| ${VAR/#The/A}  | A quick brown fox jumped over the fox  |
| ${VAR/%fox/dog}  | The quick brown fox jumped over the dog  |

</br>


## More Pattern Matching 

### Pattern Matching 

| Operator | Meaning |
|---|---|
| * | Matches any string including the null.  |
| ?  | Matches single character |
| [a-Z] | Matches case insensitive letters a - z |
| [0-9a-Z] | Matches case insensitive letters and numbers |
| **/* | Matches all files and zero or more directories and subdirectories |
| **/** | Matches only directories and subdirectories |


### Posix Classes 

| Operator | Meaning |
|---|---|
| [[:alnum:]] | matches alphabetic or numeric characters. This is equivalent to [A-Za-z0-9] |
| [[:alpha:]] | matches alphabetic characters. This is equivalent to [A-Za-z] |
| [[:space:]] | matches whitespace characters (space and horizontal tab) |
| [[:cntrl:]] | matches control characters |
| [[:digit:]] | matches (decimal) digits. This is equivalent to [0-9] |
| [[:lower:]] | matches lowercase alphabetic characters. This is equivalent to [a-z] |
| [[:print:]] | Matches characters in the range of ASCII 32 – 126 (printable characters) |
| [[:upper:]] | matches uppercase alphabetic characters. This is equivalent to [A-Z] |
| [[:xdigit:]] | matches hexadecimal digits. This is equivalent to [0-9A-Fa-f] |
| ls [[:digit:]] | grep [[:digit:]] test.file |


### Extended Pattern Matching 

| Operator  | Meaning |
|---|---|
|  *(pattern) | Matches zero or more occurrences of the given pattern |
|  +(pattern) | Matches one or more occurrences of the given pattern |
|  ?(pattern) | Matches zero or one  occurrence of the given pattern |
|  @(pattern) | Matches exaclty one of the given pattern |
|  !(pattern) | Matches anything except one of the given pattern |


ls -d !(*.html|*gif|*jpg) # everything but .html, .jpg or ,gif files  
ls file+([0-9])           # list file9, file22 but not fileit   
ls -d +(apl*|un*)         # begins with apl or un only   


</br>



## Package Managers Cheatsheet 

## Common tasks 

|  | APT  | YUM  |
|---|---|---|
| Install package from repo  | apt install <package>  | yum install <package>  |
| Install package from file  | dpkg -i <package.deb>  | yum localinstall <package.rpm>  |
| Install package group  | apt install <meta package>  | yum group install <group>  |
| Reinstall package  | apt-get --reinstall install <package>  | yum reinstall <package>  |
| List software groups  | NA  | yum group list  |
| Remove package  | apt remove <program name>  | yum remove <program name>  |
| Remove package group  | apt remove <meta package>  | yum group remove <group>  |
| Search for package  | apt search <program name>  | yum search <program name>  |
| Search for file  | apt search <file name>  | yum provides <file>  |
| Display package info  | apt info <package>  | yum info <package>  |
| Update package  | apt install <package>  | yum upgrade <package>  |
| Update repository  | apt update   | yum check-update  |
| Upgrade system  | apt upgrade  | yum upgrade  |
| Upgrade distribution  | apt full-upgrade  | yum upgrade  |
| Remove a package  | apt remove <program name>  | yum remove <program name>  |
| List Installed packages  | apt list --installed  | yum list installed  |
| List repositories  | cat /etc/apt/sources.list  | yum repolist  |
| Add repository  | edit /etc/apt/sources.list  | edit /etc/yum.repos.d/<repo file>  |

</br>

## Local Package Management

|  | DEB  | RPM  |
|---|---|---|
| Install package file  | dpkg -i <package.deb>  | rpm -i <package.rpm>  |
| Upgrade package file  | dpkg -i <package.deb>  | rpm -U <package.rpm>  |
| Upgrade only if installed  | NA  | rpm -F <package.rpm>  |
| Remove package  | dkpg -r <program name>  | rpm -e <program name>  |
| Show all installed packages  | dpkg -l  | rpm -qa   |
| List files in installed package  | dpkg -L <program name>  | rpm -ql <program name>  |
| List files in uninstalled package  | dpkg -c <package.deb>  | rpm -qlp <package.rpm>  |
| Show info of installed package  | dpkg -p <program name>  | rpm -qi <program name>  |
| Show info of uninstalled package  | dkpg -I <package.deb>  | rpm -qip <package.rpm>  |
| Verify package  | NA  | rpm -V <program name>  |
|List files in installed package | dpkg -L <program name> | rpm -ql <program name> |
| List files in uninstalled package | dpkg -c <package.deb> | rpm -qlp <package.rpm> |
| Show info of installed package | dpkg -p <program name> | rpm -qi <program name> |
| Show info of uninstalled package | dkpg -I <package.deb> | rpm -qip <package.rpm> |
| Verify package | NA | rpm -V <program name> |

</br>

## Regex Cheatsheet

| Anchors  | Description   | Example  | Matches  |
|---|---|---|---|
| ^  | Matches beginning of line  | '^This'   | This dog has a tail  |
| $  | Matches end of line  | 'tail$'  | This dog has a tail  |
   
</br>

###  Character Classes and Sets
| [123,%abc]   | Any one character in the []  | [0-9] [a-z]  | Range  |
|---|---|---|---|
| [^abc]  | Not any one character in the []  | [-^abc]  | Hyphen, caret or abc  |
| [:alpha:]  | Alphabetical character a-z A-Z  | [:alnum:]  | a-z, A-Z, or 0-9  |
| [:blank:]  | Space or tab  | [:digit:]  | 0-9  |
| [:lower:]  | Lowercase  a-z  | [:upper:]  | Uppercase A-Z  |
| [:print:]  | Printable character  | [:punct:]  | Any punctuation  |
| [:space:]  | Any space – Tab, NL, FF, VT, CR  | [:xdigit:]  | Hexidecimal digits  |
 
</br>

### Basic Regular Expressions (sed, grep)
| Pattern  | Match  | Pattern  | Match  |
|---|---|---|---|
| .  | 1 character  | \{2,4\}  | 2-4 of previous character  |
| *  | 0 or more of previous character  | \(ab\)  | Match group of chars (ab)  |
| \{0,1\}  | 0 or 1 of previous character  | \(ab\)\{2\}  | Multiple groups  |
| \{1,\}  | 1 or more of previous character  |   |  |
| \{2\}  | 2 of previous character  |   |  |

</br>

### Extended Regular Expressions (sed -r, egrep, awk, bash [[ =~ ]])
| Pattern  | Match  | Pattern  | Match  |
|---|---|---|---|
| .  | 1 character  | {2,4}  | 2-4 of previous character  |
| *  | 0 or more of previous character  | (ab)  | Match group of chars (ab)  |
| ?  | 0 or 1 of previous character  | (ab){2}  | Multiple groups  |
| +  | 1 or more of previous character  | (cat\|dog)  | Match cat or dog  |
| {2}  | 2 of previous character  |  |   |

</br>

###  BASH_REMATCH and back references
| Mechanism  | Description  | Match  |
|---|---|---|
| [[ photo.jpg =~ ^(.*)\.([a-Z]*)$ ]]   | Entire string is saved in ${BASH_REMATCH}  | photo.jpg  |
| 1st match (.*) is saved in ${BASH_REMATCH[1]}  | photo  | 2nd match ([a-Z]*) is saved in ${BASH_REMATCH[2]}  | jpg  |
| egrep '^(.?)(.?).?\2\1$'  |
| Matches in () are saved for recall in back references.   |
| The first match is saved in \1, second in \2 ...  |
| (.?)(.?).?\2\1 = (first)(second)third(second)(first)  |	radar		civic  		kayak  |


</br>

## Linux RPM Cheat Sheet

| Installing, Upgrading, Remove Software  | Function  |
|---|---|
| rpm -i <package.rpm>  | Install software  |
| rpm -U <package.rpm>  | Upgrade software. Install if it isn't already  |
| rpm -F <package.rpm>  | Freshen software. Update only installed software  |
| rpm -e <package.rpm>  | Remove software  |
|  -v  | Be verbose  |
| --nodeps  | don't check dependencies  |
| -h  | Print progress (hashes)  |
| --test  | Test run  |
| --force  | Overwrite other files and packages  |

</br>

| Querying  | Function  |
|---|---|
| rpm -q  | Query   |
| rpm -qa  | Queries all installed packages  |
| rpm -ql <packagename>  | Lists all files belonging installed package.  |
| rpm -qlp  | Lists all files that are in the rpm.  |
| rpm -qi <packagename>  | Shows information on the installed package.  |
| rpm -qip <package.rpm>  | Shows information on the rpm.  |
| rpm -qf <filename>  | Query package that owns <filename>  |
| rpm -q --whatprovides <file>  | Find package that provides <file>  |

</br>

| Verifying and Checking  | Function  |
|---|---|
| rpm -V <packagename>  | Verify - checks to see if installed package has changed in any way since it was installed.  |
| rpm -Va  | Verify all  |

</br>

Checks for and displays:
- S Size differs
- M Mode differs (includes permissions and file type)
- 5 MD5 sum differs
- D Device major/minor number mis-match
- L ReadLink path mis-match
- U User ownership differs
- G Group ownership differs
- T mTime differs
rpm -K <package.rpm>
Checks PGP sig to see if package is actually from who it says it's from and that the package.rpm is intact. 


</br>

## Disk Tools Cheat Sheet

| Function | Description |
|---|---|
| fdisk/sfdisk/cfdisk | Legacy disk tools for BIOS systems (sfdisk for scripts) |
| gdisk/sgdisk/cgdisk | Disk tools for UEFI/GTP systems (sgdisk for scripts) |
| parted | Advanced disk tool with filesystem options |

</br>

| Disk Tool Function | fdisk | gdisk | Parted|
|---|---|---|---|
| Help menu | m | ? | help |
| Print partitions on screen | p | p | print |
| Create partition | n | n | mkpart TYPE START END |
| Create partition with FS | | | mkpartfs TYPE FS-TYPE START END |
| Make FS on partition | | | mkfs NUMBER FS-TYPE |
| Show detailed info | | i |  print all |
| Delete partition | d | d | rm <number> |
| List partition types | l | l | |
| Change partition type | t | t | |
| Expert menu | x | x | |
| Transpose partitions | | xt | move NUMBER START END |
| Resize partition || xs | resize NUMBER START END |
| Replicate partition table | | x u | |
| Verify disk | v | v | |
| Write table to disk | w | w | |
| Quit | q | q | quit |

</br>

| Other Disk Tools | Description |
| ---|--- |
| lsblk | Lists block devices in tree format |
| blkid | Lists block devices with UUID and filesystem type |
| partprobe | Forces the kernel to re-probe the disks |
| fixparts/testdisk | Fix and restore partitions and files |
| wipefs/shred | Zero the disk, erasing all files or erasing a single file |
| mkfs,mke2fs | Makes filesystem on partition (format) |
| tune2fs | Changes filesystem options |
| fsck | Checks filesystem |
| mkswap | Makes swap partitions |
| dd/ddrescue/dd-rescue | Duplicate disks 


</br>

## firewalld Cheat Sheet
### Zone Concept
Any network packet entering in the network stack is associated with a zone.
• If the packet comes from a network address bound to a zone, then it is associated with this zone.
• If the packet comes from a network interface bound to a zone, then it is associated with this zone.
• Otherwise, the packet is associated with the default zone.
| Zone Management | Command |
| ---|--- |
| Check status | systemctl status firewalld |
| Get default zone | firewall-cmd --get-default-zonefirewall-cmd --get-active-zones |
| List zones with interfaces | firewall-cmd --get-active-zones |
| List all zones | firewall-cmd --get-zones |
| Change default zone | firewall-cmd --set-default-zone=home |
| Add interface to zone | firewall-cmd --permanent --zone=internal --change-interface=eth0 |
| Modify zone | nmcli con mod "System eth0" connection.zone internal |
| Bring up zone | nmcli con up "System eth0" |
| List zone for eth0 | firewall-cmd --get-zone-of-interface=eth0 |
| List permanent info | firewall-cmd --permanent --zone=public --list-all |
| Create new zone | firewall-cmd --permanent --new-zone=test |
| Remove source from zone | firewall-cmd --permanent --zone=trusted --re- |
| move-source=192.168.2.0/24 |
| Add service to zone | firewall-cmd --permanent --zone=internal --add-service=http |
| Add port 443 to zone | firewall-cmd --zone=internal --add-port=443/tcp |
| Add new service | firewall-cmd --permanent --new-service=haproxy |
| Create direct rule | firewall-cmd --direct --add-rule ipv4 filter INPUT 0 -p tcp --dport 9000 -j ACCEPT |
| Reload firewall | firewall-cmd --reload |


## Important Linux Config files

</br>

### /etc/group

root:x:0:
bin:x:1:daemon
daemon:x:2:
sys:x:3:
tty:x:5:
haldaemon:!:102:
nobody:x:65533:
nogroup:x:65534:nobody
users:x:100:

The /etc/group contains information on the the system groups. Included is:

| Field | Contents |
|---|---|
| 1 | Group name |
| 2 | support for group shadow password (stored in /etc/gshadow but not currently used) |
| 3 | Group id number (GID) |
| 4 | Users that belong to the group |

</br>

### /etc/passwd

root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
ldap:x:55:55:LDAP User:/var/lib/ldap:/bin/false
ftpsecure:x:501:501::/home/ftpsecure:/sbin/nologin
dude:x:502:502::/home/dude:/bin/bash

The /etc/passwd contains the account information for each user. Included is:

| Field | Contents |
|---|---|
| 1 | Login name |
| 2 | x if the shadow suite is installed. Encrypted password if it's not. |
| 3 | User ID number (UID) |
| 4 | Group ID number (GID) |
| 5 | Comment |
| 6 | Home directory of user |
| 7 | Login shell 

</br>

### /etc/shadow

at:!:13047:0:99999:7:::
bin:*:13047::::::
daemon:*:13047::::::
lp:*:13047::::::
nobody:*:13047::::::
ntp:!:13047:0:99999:7:::
postfix:!:13047:0:99999:7:::
root:$2a$05$bNKG567WQ8h2P4e58DBZ.OCDLo1wAQrPY6Zg2uuyFz5xgryL/r7eS:13047::::::
sshd:!:13047:0:99999:7:::
uucp:*:13047::::::
wwwrun:*:13047::::::
dude:$2a$10$wq2k7m3kkOpPQVEd1FixeuORbZNb44IjD9m2NJHdCHrMPs9JVmzri:11:0:99999:7:::

The /etc/shadow contains the encrypted password information for user's accounts and optional the
password aging information. Included is:

| Field | Contents |
|---|---|
| 1 | Login name |
| 2 | Encrypted/encoded password (EDS, 3DES, MD5, Blowfish) |
| 3 | Days since Jan 1, 1970 that password was last changed |
| 4 | Days before password may be changed |
| 5 | Days after which password must be changed |
| 6 | Days before password is to expire that user is warned |
| 7 | Days after password expires that account is disabled |
| 8 | Days since Jan 1, 1970 that account is disabled |
| 9 | A reserved field |



## LVM Cheat Sheet

| Physical Volumes | Usage |  |
|---|---|---|
| pvcreate | Create a PV from disk | pvcreate /dev/sda3 |
| pvremove | Remove a PV from a disk | pvremove /dev/sda3 |
| pvmove | Move a PV to free extents in the same vg | pvmove -v /dev/sda3 |
| pvdisplay/pvs | Display info about PVs | |
| pvscan | Scan for PVs | |
| pvresize | Resize PVs to either a set size or the size of the disk/partition |pvresize --setphysicalvolumesize 40G /dev/ |
| sda3 pvresize /dev/sda3 |

</br>

| Volume Groups | Usage | |
|---|---|---|
| vgcreate | Create a VG from PVs; character sets [ ] can be used for ranges | vgcreate vgname /dev/sda3 /dev/sdb3 vgcreate vgname /dev/sd[d-m]1 |
| vgremove | Remove a VG | vgremove vgname |
| vgdisplay/vgs | Get info about VGs | |
| vgscan | Scan for VGs | |
| vgextend | Add a PV to a VG | vgextend vgname /dev/sdb2 |
| vgreduce | Scan for VGs vgreduce vgname /dev/sdb2    vgreduce --removemissing |
| vgchange  | Remove a PV from a VG | vgchange -u vgname     vgchange -ay      vgchange -an |

</br>

| Logical Volumes | Usage | |
|---|---|---|
| lvcreate | Create an LV        Create an LV with stripe        Create an LV with mirror(s)         Create the largest LV possible  |
 lvcreate --name lvname --size 50G vgname        lvcreate --name lvname -i3 -I4 --size 100G vgname       lvcreate --name lvname -m1 --size 50G vgname        lvcreate --name lvname -l +100%FREE vgname | 

| lvremove | Remove a VG | lvremove /dev/vgname/lvname |
| lvdisplay/lvs | Get info about VGs | |
| lvscan | Scan for VGs | |
| lvresize | Add a PV to a VG | lvresize --size 40G /dev/vgname/lvname    lvresize -l +100%FREE /dev/vgname/lvname |

</br>

| Miscellaneous |
| Path to logical volume /dev/vgname/lvname       /dev/mapper/vgname-lvname |


</br>

## LVM Advanced Cheat Sheet

| Logical Volumes | Usage |
| ---|--- |
| Create a RAID0 LV | lvcreate --name lvname --stripes 3 --stripesize 4 --size 100G vgname |
| Create a RAID5 LV | lvcreate --type raid5 --stripes 3 --size 1G --name lvname vgname |
| Create a RAID10 LV | lvcreate --type raid10 --stripes 2 --mirrors 1 --size 10G --name lvname vgname |
| Create an LV with mirror(s) | lvcreate --name lvname --mirrors 1 --size 50G vgname |
| Split LV from mirror | lvconvert --splitmirrors 2 --name copy /dev/vgname/lvname |
| Add tag to LV | lvchange --addtag grouptag /dev/vgname/lvname |

</br>

| Volume Groups | Usage |
|---|---|
| Split a VG | vgsplit vgname newvg /dev/sdb1 |
| Combine VGs | vgmerge -v newvg oldvg |
| Move volume group to new host | vgchange -an vgname   vgexport vgname |

</br>

| Snapshots | Usage |
|---|---|
| Create snapshot | lvcreate --size 100G --snapshot --name snap /dev/vgname/lvname |
| Create thin-provisioned snap-shot of thin-provisioned | volume lvcreate --shapshot --name thinsnap /dev/vgname/thinlvname |
| Merge snapshot | lvconvert --merge /dev/vgname/snap |
| Merge all snapshots with tag | lvconvert --merge @grouptag |

</br>

| Cache Volumes | Usage |
|---|---|
| Create cache data volume | lvcreate -L 2G -n lv_cache VG /dev/sdf1 |
| Create cache metadata volume | lvcreate -L 12M -n lv_cache_meta VG /dev/sdf1 |
| Create cache pool | lvconvert --type cache-pool --cachemode writethrough --poolmetadata VG/lv_cache_meta VG/lv_cache |
| Create cache logical volume | lvconvert --type cache --cachepool VG/lv_cache VG/lv |
| Create thin pool on cached volume | lvconvert --thinpool vg/cvol |

</br>

## Mounting Cheat Sheet

| Task | Command |
|---|---|
| Show device messages. | dmesg | less |
| Show block devices. | lsblk, blkid |
| Show raw block devices. | cat /proc/partitions |
| Show mounted devices. | df or mount |
| Mount all devices in /etc/fstab. | mount -a |
| Mount device in /etc/fstab. | mount <device path> or mount <mountpoint path> |
| Unmount device. | unmount <device path> or unmount <mountpoint path> |
| Mount with multiple options. | mount -o acl,rw <device path> <mountpoint path> |
| Find locks on mounted devices. | fuser <mountpoint path> or <device path> |
| Find locks on mounted devices. | lsof | grep <mountpoint> |

</br>

| Mount Type | Device Path |
|---|---|
| IDE disk | /dev/hda1 |
| SATA, SCSI, USB, FireWire | /dev/sda1 |
| CD-ROM writable | /dev/sr0 |
| Disk by label | /dev/disk/by-label/root |
| Disk by UUID | /dev/disk/by-uuid/bc5fbb9a-5e6e-46a0-9636-452129350168 |
| Disk by ID | /dev/disk/by-id/dm-name-VolGroup00-LogVol00 |

</br>

| Filesystem Type | Command |
|---|---|
| Windows Fat32 | mount -t vfat /dev/sdb /media/disk/ |
| Optical disk (CD/DVD) | mount -t iso9660 /dev/sr0 /media/cdrom/ |
| Windows network drive | mount -t cifs //computer/share /mnt/smbshare/ |
| Unix network drive | mount -t nfs computer:/share /mnt/nfsshare/ |
| Disk file | mount -o loop diskfile.img /media/diskfile/ |

</br>

| Filesystem | Mount Option |
|---|---|
| Windows filesystems | fat, vfat, exfat, ntfs |
| Linux filesystems | ext2, ext3, ext4, xfs, btrfs |
| Network filesystems | cifs, nfs, gfs2 |

</br>

### Example /etc/fstab

| Device | Mountpoint | Filesystem | Options | dump? | fsck? |
|---|---|---|---|---|---| 
| /dev/sda1 | / | ext4 | defaults,acl | 1 | 1 |
| /dev/scd0 | /media/cdrom | iso9660 | user,exec | 0 | 0 |
| fs:/var/share | /var/share | nfs | defaults | 0 | 0  |


</br>

## Network Tools Cheat Sheet

| Task | New | Legacy |
| ---|---|--- |
| IP/Netmask/MAC | | | |
| Set IP address. | ip addr add 192.168.1.100/24 dev eth0 | ifconfig eth0 192.168.1.100 |
| Set netmask. | ip addr add 192.168.1.100/24 dev eth0 | ifconfig eth0 netmask 255.255.255.0 |
| Set MAC. | ip link set dev interface address 00:07:e9:0c:ec:5e | ifconfig eth0 hw ether 00:07:e9:0c:ec:5e |
| Request DHCP address. | dhclient eth0 | |
| Set default gateway. | ip route add default via 192.168.1.1 | route add default gw 192.168.1.1 |
| Show default gateway. | ip route | route |
| Show network device settings. | ip link | ethtool eth0 |
| Show IP address. | ip addr show | ifconfig |
| Show netmask. | ip addr show | ifconfig |
| Check routing. | traceroute 4.2.2.2 |  |
| Restart network nervice. | systemctl restart network service | network restart |

</br>

### ARP, Connectivity, and Ports 
| Check connectivity. | ping 192.168.1.100 |
| ---|--- |
| Check connectivity (broadcast). | ping -b 192.168.1.255 |
| Show ARP table. | arp |
| Set static ARP entry. | arp -s 192.168.1.100 00:07:e9:0c:ec:5e |
| Deleting an ARP entry. | arp -d 192.168.1.100 |
| Show network connections. | ss -ltn netstat -platune |
| Scan network ports. | nmap -sT -sU -P0 -O 192.168.1.100 |

</br>

### DNS
| Resolve DNS name (address record). | dig google.com A | nslookup google.com |
| ---|---|--- |
| Resolve DNS using server. | dig @4.2.2.2 google.com | nslookup google.com 4.2.2.2 |


</br>

## Processes Cheat Sheet

| Command | Purpose |
|---|---|
| ps -ef | Show every process with full output. |
| ps -ejH | Show process hierarchy (tree). |
| pstree | Show more graphical process tree. |
| ps -efL | Show process threads. |
| ps -efZ | Show processes with SELinux security context. |
| ps -u root -f | Show all processes run by the user root with full output. |
| ps -eo pid,ni,pri,stat,comm | Show customizable output fields. |
| ps -C salt-master -o pid= | Show process IDs of a specific process (salt-master). |
| ps -p 25409 -o comm= | Show only the name of process ID 25409. |
| ps -f -t tty1 | Show all processes running on a certain terminal (tty1). |
| ps -eo pid,user,args --sort user | Show all process ids, users. and args sorted by user. |
| ps -u root -eo start,pid,args | Show all processes args run by a user with start time. |
| pgrep -u root sshd | Grep for SSHD processes run by root. |
| pgrep -u root,bob sshd | Grep for SSHD processes run by root OR bob. |
| ps -fp $(pgrep -d, -x salt-master) | Give detailed statistics on all salt-master processes. |
| kill 25045 | Kill process 25045 nicely. |
| kill -9 25045 | Kill process 25045 forcibly. |
| kill -HUP 25045 | Send process 25045 hangup signal (reread config). |
| pkill salt-master | Kill all processes named salt-master nicely. |
| pkill -9 salt-master | Kill all processes named salt-master forcibly. |
| kill -HUP salt-master | Send process named salt-master hangup signal. |
| nice -10 cp | Run cp with a nice level of +10. |
| nice --10 cp | Run cp with nice level of -10. |
| renice -10 cp | Change nice value of running process (cp). |
| top | Show top processes by resource. |
| lsof | List open files (running programs from disk). |
| lsof -u root | List open files owned by root. |
| nohup cp -av /media /backup & | Run a command that will survive a logout. |
| pidof crond | List process ID of crond. 


</br>

## SELinux Cheat Sheet

| RPM Packages | Purpose |
|---|---|
| setroubleshoot | RPM for setroubleshootd and sealert |
| policycoreutils-gui | RPM for system-config-selinux |
| setools | RPM for seaudit and apol |
| policycoreutils-python | RPM containing policy create scripts |

</br>

| Commands | Purpose |
|---|---|
| /etc/sysconfig/selinux | Config file |
| /etc/selinux | Policy locations |
| setroubleshootd | Translates AVC denial messages in audit.log |
| /var/log/audit/audit.log | Log of all SELinux messages |
| /var/log/messages | Log of all denials if setroubleshootd is running |
| sealert -a audit.log -H > file.html | Creates HTML webpage out of audit.log |
| setenforce | Sets mode of SELinux in real time |
| sestatus | Tool to show you the status of SELinux |
| seinfo -c | Prints list of object classes |
| seinfo -t | Prints list of object types |
| seinfo -u | Prints list of SELinux users |
| seinfo -n | Prints list of network contexts |
| seinfo -p | Prints list of network port contexts |
| seinfo -b | Prints list of Booleans |
| getsebool -a | Gets list of Booleans and current setting |
| setsebool <boolean> <on \| off> | Sets Boolean, use -P to make persistent |
| restorecon <file> | Restores files to default security context |
| chcon -t <context_t> <file> | Sets context of <file> to <context_t> |
| ls -Z <file> | Lists sSecurity cContext of oObject |
| ps -AZ | Lists sSecurity cContext of sSubjects |
| id -Z | Lists sSecurity cContext of uUser |
| system-config-selinux | Red Hhat GUIui pPolicy mManagement tool |
| semanage | Command-line Policy Management tool |
| checkpolicy | Compiles policy into binary for the kernel |
| audit2allow | Creates policy modules |
| semodule -i <policy module> | Inserts policy module created by audit2allow |

</br>

### Audit2allow example 
| grep http audit.log | audit2allow -m local && semodule -i local.pp 


</br>

## Secure Shell Cheat Sheet

| Task | Command |
| ---|--- |
| Logging in | |
| Connect to remote host. | ssh 192.168.1.100 |
| Connect as another user. | ssh -l bob 192.168.1.100 |
| Connect on alternate port number. | ssh -p 1022 192.168.1.100 |
| Combine all of the above. | ssh bob@192.168.1.100:1022 |
| SSH Options | |
| Connect with alternate cipher. | ssh -c blowfish 192.168.1.100 |
| Connect and forward X traffic. | ssh -X 192.168.1.100 |
| Execute command remotely. | ssh 192.168.1.100 “tail /var/log/messages” |
| Secure Copy | |
| Copy files securely. | scp file.tar.gz 192.168.1.100:/home/ |
| Copy files as another user. | scp file.tar.gz bob@192.168.1.100:/home/ |
| Copy files with alternate cipher. | scp -c blowfish file.tar.gz 192.168.1.100:/home/ |
| Copy files on alternate port number. | scp -P 1022 file.tar.gz 192.168.1.100:/home/ |
| Copy files and preserve permissions. | scp -p file.tar.gz 192.168.1.100:/home/ |
| Copy recursively. | scp -r /home/user 192.168.1.100:/home/ |
| Key - Based Authentication | |
| Create new SSH keys. | ssh-keygen -t dsa |
| Cache SSH keys. | ssh-agent |
| Add identity to ssh-agent. | ssh-add |
| SSH Files | |
| SSH server configuration | /etc/ssh/sshd_config |
| SSH client configuration | /etc/ssh/ssh_config |
| User Private/public keys | ~/.ssh/id_dsa, ~/.ssh/id_dsa.pub |
| Public keyring | ~/.ssh/authorized_keys |
| Known hosts | ~/.ssh/known_hosts |
| Port Forwarding | |
| Forward local 8080 to remote host 80. | ssh -L 8080:remote.server.com:80 bob@remote.server.com |
| Forward remote 1022 to local 22. | ssh -R 1022:remote.server.com:22 bob@remote.server.com |


</br>

## Systemd Services Cheat Sheet

### Services

| Common Tasks | Systemd | Legacy Red Hat | Legacy Debian |
|---|---|---|---|
| Start service. | systemctl start httpd | service httpd start | /etc/init.d/httpd start |
| Stop service. | systemctl stop httpd | service httpd stop | /etc/init.d/httpd stop |
| Restart service. | systemctl restart httpd | service httpd restart | /etc/init.d/httpd restart |
| Reload service config. | systemctl reload httpd | service httpd reload | /etc/init.d/httpd reload |
| Show service status. | systemctl status httpd | service httpd status | /etc/init.d/httpd status |
| Show status of all services. | systemctl list-units -t service --all | service --status-all | NA |
| Start service on boot. | systemctl enable httpd | chkconfig httpd on | update-rc.d httpd enable |
| Disable service on boot. | systemctl enable httpd | chkconfig httpd off | update-rc.d httpd disable |
| Add to runlevel. | systemctl enable httpd | chkconfig httpd --level 3 | update-rc.d httpd enable 3 |
| Show all services. | systemctl list-unit-files -t service | chkconfig --list | rcconf --list |
| Show modified services. | systemd-delta | NA | NA |
| Show details of service. | systemctl show httpd | NA | NA |
| Block service. | systemctl mask httpd | NA | NA  |
| Unblock service. | systemctl unmask httpd | NA | NA |
| Enable service | systemctl is-enabled httpd | chkconfig --list \|grep httpd | ls /etc/init.d/rc.d/rc3.d/S* |
|
</br>

### Runlevels/Targets
| Common Tasks | Systemd | Legacy Red hat | Legacy Debian |
| ---|---|---|--- |
| Change to runlevel. | systemctl isolate basic.target | init 3 | init 3 |
| Change to rescue mode. | systemctl rescue | init 1 | init 1 |
| Set default runlevel. | systemctl set-default user.target | vi /etc/inittab | vi /etc/inittab |
| Show current runlevel. | systemctl list-units -t target | runlevel | runlevel |
| Get default runlevel. | systemctl get-default | grep default /etc/inittab | grep default /etc/inittab |
| Power off system. | systemctl poweroff | shutdown -h now | NA |
| Halt system (don'tpower off). | systemctl halt | NA | NA |
| Reboot system. | systemctl reboot | shutdown -r now | NA |
</br>

| Miscellaneous| |
| ---|--- |
| Run systemd commands remotely. | systemctl --host user@host_name command |
| Analyze boot performance. | systemd-analyze blame |