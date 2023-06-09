##
# Linux Command Line
##

A command line, or terminal, is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text.

The command line typically presents you with a prompt. As you type, it will be displayed after the prompt. Most of the time you will be issuing commands. 


## Basic Commands

- ```date```: current date
- ```cal```: current months calendar
- ```cal 1999```: calendar for 1999
- ```cal -3```: calendar (last month, current and next month)
- ```cal -y```: all year calendar
- ```clear```: clear console text
- ```exit```: exits de terminal


## Uname Command

The uname or unix name command will print detailed information about your Linux system and hardware. This includes the machine name, operating system, and kernel. To run this command, simply enter uname into your CLI.

Here’s the basic syntax:

uname [option]

These are the acceptable options to use:

-a prints all the system information.

-s prints the kernel name.

-n prints the system’s node hostname.


## Hostname command

Run the hostname command to know the system’s hostname. You can execute it with or without an option. Here’s the general syntax:

hostname [option]

There are many optional flags to use, including:

-a or –alias displays the hostname’s alias.

-A or –all-fqdns displays the machine’s Fully Qualified Domain Name (FQDN).

-i or –ip-address displays the machine’s IP address.

For example, enter the following command to know your computer’s IP address:

hostname -i

## Navigate Directories

### Linux File System Tree:

- **bin**: binary (commands and utilities that all users can run)
- **sbin**: this directory contains programs that performs vital system tasks (network management, disk partitioning). Only the superuser has access to these programs.
- **home**: each user is given a directory under the home directory. A user can store anything in his home directory
- **opt**: optional (additional software)
- **tmp**: temporary files, files created by various programs (**Generally cleared on reboot**)
- **var**: variable data, data that frequently changes over time.
  - Log files
  - Data bases
  - User mail
  - Spools -> temporary storage location
    - /var/spool is traditionally used for machine-local data being spooled to or from UNIX subsystems. For example, print jobs are spooled here for delivery to the lineprinter daemon, out-bound mail is spooled for delivery to remote systems, and UUCP files are spooled for transmission to UUCP neighbors. In-bound mail and news are spooled here for delivery to users, and at and cron jobs are spooled for delayed execution by the cron daemon.


_ABSOLUTE VS RELATIVE PATHS_

An absolute path begins with the root directory
> EXAMPLE  /home/john/documents/phone.txt

A relative path starts from the current working directory
> EXAMPLE     ./documents/phone.txt

You can omit the ./ because it is already implied


### Commands

- ```pwd```: print working directory

- ```ls```: list directory

- ```cd```: change directory

- ```cd /```: take you to the root directory

- ```cd ~```: take you to the user home directory

- ```cd ./another_folder```: navigate from current directory to another_folder

- ```cd ..```: navigate from current directory to parent directory

- ```cd -```: go back to the previous working directory
  - ```cd /```: going to the root directory
  - ```cd ~/```: going to the home directory
  - ```cd -```: going back to the root directory


- ```cd "my work"``` or ```cd 'my work'``` or ```cd my\ work```: going to a folder with space

- ```ls /```: display your root directory

- ```ls ~```: display your home directory

- ```ls ..```: display the content of my parent directory

- **[DOES NOT WORK]** ```ls -```: should display you the content of your previous working directory

#
.  _This directory_


.. _Parent directory_

#

- For example ls -1 file1.txt can have the following output

![image](https://github.com/ashrafkgit/Linux/assets/134578702/da880cfa-5472-44dd-8937-2f3bab1a9a65)


## Linux Links

- Every file in the system has an inode (Index node)
  - Contains all file information except the file content and name  
  - A database of a file
  - They contain:
    - Inode number
    - File size
    - Owner information
    - Permission
    - File type
    - Number of links
      - Soft Link
      - Hard Link
    - etc...

### Soft Link
- A soft link is the same as a shortcut in Windows
- Aka Symbolic link
- It is a pointer to the original file
- It is a file pointing to another file
  - Different inode number
- Small file size
- In case the original file gets deleted, the soft link will no longer work
- You can create soft links for directories

![image](https://github.com/ashrafkgit/Linux/assets/134578702/2bb248e8-8352-4fd3-86ac-6e49bb4555b7)

### Hard Link
- Different name of the same file
- Same file size
- Same inode number
- You cannot differentiate between a real file and a hard link
- They are kind of a copy of the file
- If I change a hard link file content, it will reflect on the other files (the original and other hard links)
- In case I delete the original file, the hard link file will still work
- **Be careful**: You should not create hard links for directories. Normally they are not even allowed because they break the file system structure.

![image](https://github.com/ashrafkgit/Linux/assets/134578702/2cb6dcf6-9884-46ca-a714-6f890dd9d185)

### Commands

- ```ls -i```: show inode id of files

- ```ls -l```: show files information (size in bytes, permission, etc.)
  _Folders should start with the letter_ `d` 
  ![image](https://github.com/ashrafkgit/Linux/assets/134578702/d5d9ada8-583f-420e-b3aa-3445784c6c2a)

- ```ln```: link

- ```ln file_name hard_link1```: Create a hard link for a file (same inode)

- ```ln -s file_name soft_link1```: Create a soft link for a file

- ```ln -s .. c```: Create a soft link C for the parent directory you are currently located in

## LS Options

- ```ls```: List files by alphabetic order

- ```ls -i```: This will list the index node number of each file

- ```ls -a```: This will show all the files (-a == all files) in your current directory, including hidden files

- ```ls -l```: Long listing of all files in the directory and some important information details permissions, owner, size, last modified date and name of the file

- ```ls -t```: Sort files by modification date

- ```ls -r```: List the files in reverse fashion (in this case reverse based on alphabetic order)

- ```ls -rt OR ls -r -t```: List the file in reverse fashion (in this case reverse based on modification date)

- ```ls -li```: Long listing + show inode ids

- ```ls -lia```: Long listing + show inode ids + hidden files

- ```ls -R```: Show current directory content plus any children/sub directory content as well

- ```ls -Ra```: Show current directory content plus any children/sub directory content as well + including hidden files'

-  ```ls -F```: list files types

#
_Note: Avoid using white space for file names ( such files can be searched by single or double quotes with ls command)_
#


## Touch Command (Create a file)

- Touch is used to create empty files

  - ```touch file_name```: Create a file called file_name
  - ```touch file_name1 file_name2 file_name3```: Creates 3 files
  - ```touch 'my file'``` or ```touch "my file"``` or ```touch my\ \ file```: create a file with a name containing spaces
    - ```\``` is a scape sequence


- Touch is also used to update a current files timestamp (modification dade)

  - ```touch newFile```
  - ```echo "test" > newFile```
  - ```touch newFile```: this will update the file timestamp and keep the content


![image](https://github.com/ashrafkgit/Linux/assets/134578702/c69234e7-5fd6-4a66-8a30-4f1b194ce653)

## MKDIR (Make directory) and RMDIR (Remove directory) Commands

- If you want to create a directory, then you use ```mkdir``` command as follow:

  ```
  mkdir directory_name
  mkdir directory_name1 directory_name2 directory_name3
  ```

- To remove **empty** directories you can use ```rmdir``` command as follows:

  ```
  mkdir empty_dir
  rmdir empty_dir
  ```

  - In case you do ```rmdir``` in one directory that has files and another that is empty, it will only delete the empty one.


- To create a directory with a name containing spaces, you can do ```mkdir 'my directory'``` or ```mkdir "my directory"```

## RM (Remove) Command

  - To delete non-empty-directory files, or just normal files you just do:
    ```
    touch fileToDelete
    rm fileToDelete
    mkdir folder
    cd folder
    touch file
    cd ..
    ```
    - ```rm -R folder``` or ```rm -r folder```

    - In case of non-empty-directory you need to run ```rm``` with the recursive flag ```-R```. Otherwise it will fail
    - Also, the ```-R``` flag can be lowercase since it is not case sensitive for ```rm``` (although it is case sensitive for ```ls```)


  - ```rm``` options:

    - ```rm -i```: Prompt you before removing any existing file. the ```-i``` means interactive mode

    - ```rm -f```: Never prompt you before removing a file. And will not display a warning if the file you are trying to delete does not exist, meaning that it will ignore non existent files. -f means force

    - ```rm -v```: Verbose mode. It will print the name of each file before removing it.

    - ```rm -R``` or ```rm -r```: Recursively delete files. If the file is a directory, remove the entire directory and all its contents, including subdirectories.

## CP (Copy) Command

- The ```cp``` command copies files or directories. It can be used in two different ways:
  - Copy a file: ```cp file file2```
  - Make a copy of a directory: ```cp -R dir dir2```: ```dir2``` does not need to exist
    - This will make a copy of dir1 named dir2 (Assuming that dir2 didn't exist)

  -  In case you copy many files using the following syntax:
    - ```cp file1 file2 file3 dir```: ```dir``` must exist in this case.
    - Same case for directories: ```cp -R dir1 dir2 dir3```


- ```cp``` options:

  - ```cp -i```: Before overwriting an existing file, prompt the user for confirmation. **cp will silently overwrite files by default.**
  - ```cp -v```: Verbose mode (print the name of each file that was copied).
  - ```cp -R```: Recursively copy directories and their content. Just like the ```rm``` command, this option must be specified when copying a directory.
  - ```cp -r```: Same as cp -R


## MV (Move) Command

- The ```mv``` command can be used in two different ways.
  - Renaming files

    - ```mv file1 file2```: This will rename file1 to file2
    - ```mv dir1 dir2```: If your file is a directory, this will rename the directory
    - **You do not need to use the -R option with ```mv```**

  - Moving files

    - ```mv file1 file2 dir1```: This will move file1 and file2 to dir1. However, dir1 must exist
    - ```mv dir1 dir2 dir3```: This will move dir1 and dir2 to dir3. Again, dir3 must exist


- ```mv``` options:

  - ```mv -i```: Before overwriting an existing file, prompt the user for confirmation. If the option is not specified ```mv``` **will silently overwrite the file**

  - ```mv -v```: Verbose mode (print the name of each file that was moved or renamed)

## FILE (File) Command

  - Filenames are case sensitive in just like the commands are.

  - Linux has no concept of  `file extension` like Windows. You can have files without any extension.
    - It checks the file content to identify what kind is it.


  - The command ```file filename``` will give us information about the file type.

  - ```file LS -L OUTPUT.png```: LS -L OUTPUT.png: PNG image data, 1968 x 488, 8-bit/color RGBA, non-interlaced


## Finding Files and Directories

find command 

find [ path ] [ expression ]

find -name pattern  ( finds files and directories) 

find -iname pattern ( ignore case ) 

find / -name <filname>


## Command Line History

  - ```history```: Show all the commands executed in the cmd
  - ```history 10```: Show last 10 commands
  - ```history -c```: Clear history
    - Your history is stored at ```~/.bash_history```
  - ```!number```: Runs a command from history

## Shortcuts

  - ```Control+a```: Start of the line
  - ```Control+e```: End of the line
  - ```Control+d```: Remove character from left to right
  - ```Control+l```: Clear

## View text files (less, cat, tac, head, tail) Commands

  - ```less file1```: View the content of the file ```file1```
    - Press ```q``` to quit

  - ```cat file1 file2```: View the content of the file ```file1```concatenated with ```file2```
    - ```cat``` lets you see two files output concatenated

  - ```tac file```: Shows the content of file, but reversed
  - ```head -n 20 file```: Show first 20 lines of file
  - ```tail -n 20 file```: Show last 20 lines of file
  - ```more file```      : Browse through a text file


## WC (word count) Command

  - ```wc file```: Presents the data like -> Number of lines, number of words, number of bytes
  - ```wc -l```: Show just number of lines
  - ```wc -w```: Show just number of words
  - ```wc -c```: Show just number of bytes
  - ```wc -L```: Length of longest line in characters

## Types of Commands

  - ```bash```: Born again shell

  - Executable programs
    - They are inside ```/bin``` and ```usr/bin```.
    - Example: ```cp``` command

  - Shell builtin
    - ```cd``` command
    - In computing, a shell builtin is a command or a function, called from a shell, that is executed directly in the shell itself, instead of an external executable program which the shell would load and execute.

      Shell builtins work significantly faster than external programs, because there is no program loading overhead. However, their code is inherently present in the shell, and thus modifying or updating them requires modifications to the shell. Therefore, shell builtins are usually used for simple, almost trivial, functions, such as text output.

  - Shell scripts
    - Custom programs written in shell script

  - Alias
    - ```ls``` command
    - Create your own commands
    - 	The alias command makes it possible to launch any command or group of commands (inclusive of any options, arguments and redirection) by entering a pre-set string (i.e., sequence of characters).

  - Display information about command type:
    - It displays if command is an alias, shell function, shell builtin, disk file, or shell reserved word.
    - ```type ls```: ls is hashed (/bin/ls)
    - ```type cd```: cd is a shell builtin
    - ```type cp```: cp is /bin/cp
      - ```file /bin/cp```: tells you that ```cp``` is an executable


  - ```which``` will display the path of shell scripts and executables, it does not support shell builtins.
    - ```which cp```: display executable location ```/bin/cp```


  - For shell builtin help you can do ```help cd```

  - For executable help you can do ```man cp```
    - Also for executables, you can do ```whatis cp``` to get a short description about the program


## Execute multiple commands

  - ```date; cal```: Separate commands using a semicolon
  - ```mkdir test && cd test1 && cd test```: Different from ```;``` the operand ```&&``` stops the execution if one of the commands fail (short circuit evaluation)


## Wild cards

  - ```*```: all occurrences
    - ```cp *.txt dir```
    - ```cp * dir```
  
  - `*.png` returns all the files that end with the extension .png

  - `pea?.png` returns all files that start with "pea", is followed by any single character, and end with .png (for example, peas.png and pear.png)

  - `*.{txt,pdf}` returns all files that end with either .txt or .pdf

  - `log[12345].pdf` returns files log1.pdf, log2.pdf, log3.pdf, log4.pdf and log5.pdf

  - ```?```: represents a single character
   - ```cp file?.txt dir```: copy all files file0.txt, file1.txt, etc. Any file that has a name structure like ```file``` + an unknown character + ```.txt```

  - ```[]```: range of characters
    - ```cp [abc]*.txt dir```: Copy all the file that begins with the letters abc to ```dir```

    - ```cp [!abc]*.txt dir```: Copy all the file that **does not** begins with the letters abc to ```dir```

        - Exclamation mark negates the command

    - ```cp [0-9]*.txt dir```: Copy all files starting from 0 to 9

    - ```cp [[:upper:]]* dir```: Copy all the files that starts with an upper case letter

    - ```cp [[:lower:]]* dir```: Copy all the files that starts with an lower case letter

    - ```cp *[[:digit:]] dir```: Copy all the files that ends with a digit

    - ```cp [[:alpha:]] dir```: Copy all the files that starts with a character from the alphabet

    - ```cp [[:alnum:]] dir```: Copy all the files that starts with a character from the alphabet or a number. (alpha numeric)

    - ```cp [[:alnum:]][0-9]* dir```: Copy all the files that starts with a character or a number (alpha numeric) and the second character must be a number from 0 to 9

    - ```cat ???```: View all files with exactly 3 characters

    - ```rm [[:digit]]*[abc]```: Remove all the files that begins with a number and ends with the letter (a,b or c)

    - ```rm [[:digit]]*abc```: Remove all the files that begins with a number and ends with the letters abc all together  

## Alias

  - ```alias myname="cd Desktop;mkdir dir"```: Create an alias called myname that goes to the Desktop folder and creates a directory called dir

  - ```unalias myname```: Delete an alias

  - To retain an alias, save it inside ```~/.bashrc```

  - ```alias```: List of all alias in the system

## Streams and Pipes

### Stream 

* `>` operator 
  * e.g. `grep "text" . > output.txt`
  * Writing to a file (overwrite)
  * e.g `head -n1 < /etc/passwd`
    * Using operator as input to an app

* `>>` operator 
  * e.g. `grep "text" . >> output.txt`
  * Append to a file 

### Pipes

* `ls | cowsay`
  * pipe the results from `ls` to the program `cowsay`

* `ls -l *.conf | wc -l | cowsay`

## Manage processes 

- `ps aux`
  * `a` = `--all` Display information about other users' processes as well as your own.
  * `u` = Display the processes belonging to the specified usernames.
  * `x` = When displaying processes matched by other options, include processes which do not have a controlling terminal.

- `top`

- `htop`

## Users, Groups and Permissions

* `adduser danielmapar`
  * Only root may add a user or group to the system.
  * `sudo`: `super user do`
    * `sudo -i`: login as `root`

* `sudo adduser danielmapar`
  * Executing command with root credentials 

* `sudo login danielmapar`
  * `cat /etc/passwd | grep "^danielmapar"`

![image](https://github.com/ashrafkgit/Linux/assets/134578702/d5f860d3-3a21-4847-b960-7eb9b3069106)


  * user = file owner
  * group = the group of the file owner
  * others = other users / groups
  * The first char can be `-` (for file), `d` for directory of `l` for link.

* `chmod +x file`
  * You can change the `user` and `group` permission to include `x` (execute).

* `chmod 755 file`
  * each number represents a sequence of 3 bits. In the case of 7 it represents 111 (read, write and execute). Another example is 5 (read, dont write, execute).
    * In this case, 7 changes the `user` permissions (`rwx`), the second and third numbers (5's) will change the `group` and `other` permissions respectively.

  * Another way to achieve this (`755`) is by running: `chmod u=rwx,g=rw,o=rw file`

	Permissions on file and directories is different.
	
	For files: read ( allows a file to be read), write ( allow a file to be modified), and execute ( allows a file to be executed) 
	For directories : read ( allows the contents of the directory to be read), write ( allows entries to be modified), and execute ( allows access to the contents and metadata for entries)
	
	Permissions are applied to the categories like user (u), group (g), others (o), and All (a) 
	Permission on the directory impact the permission of the files inside the directory 
	Every user will be part of at least one group and can be part of multiple groups. 
	Groups are used to modified users.
	
	Command : group ( displays user groups) 
	Command to change group : chgrp
  
  
 Commands to change permissions:
 > chmod 
 
 > ugoa
 
 > +-= 
 
 > rwx


_OCTO MODE PERMISSIONS_: Order of permission is User, Group and Other for every octal value.

![image](https://github.com/ashrafkgit/Linux/assets/134578702/8e59c7e2-a1fc-429d-a6ed-bc624d742bfc)

#
Whenever a file is created the default mask for permissions is set to 777 for directories and 666 for files, if no mask is used during creation.
	
umask -S ( subracting permission) 
	
Special modes: setuid, setgid, Sticky
#  

  
## Environment Variables and RC Files

* `echo $USER`
* `echo $HOME`
* `echo $0`
  * my shell name
* `echo $PATH`
  * Path to find binaries
  * `PATH=$PATH:newfolder`
* `env`: list of env vars

* `RC` stands for run commands.
  * `.bashrc` = Bash Run Commands.

* `export $PATH=$PATH:/newpath`
  * the keyword `export` guarantees that if our current process spins child processes, it will also export this `env` var to the children processes.

##
Notes:
Env variables has storage space, name and a value 

View all env variables command: printenv

echo $TZ --> View env Variable

printenv <variable_name> result of the output will give its value 

unset <variable_name> TZ  ---->  only affects the current running sessions, an no longer valid across login sessions.

Export VAR="value" 
Export TZ="US/PACIFIC" 

``` bash
$  cat  ~/.bash_profile 
```
Persisting environment variable. 

	
	
##
## **Create archives of the files**
##	
	

c Create a tar archive.

x Extract files from the archive.

t Display the table of contents (list).

v Be verbose.

z Use compression.

f file Use this file

tar - cxtv <file name> ( create, extract, list, verbose)

tar -f <file name that you are working with>

_List contents of tar file_
	
tar –tzf documents.tar.gz

_Create compress tar file_
	
tar -czf filename.tar filename

Example: tar -czf /jail/repository/node1.raid.tgz /var/log/hp/platform/raid/p1228*

_Extract .tar/.gz file_
.
tar –xvzf documents.tar.gz
	
_To instruct tar to put the extracted unzipped files into a specific directory, enter_
	
tar –xvzf documents.tar.gz –C /home/user/destination

	
gzip Compress files.
gunzip Uncompress files.
	
##
## Transferring files
##
	
SCP - secure copy

SCP source destination 


scp /file/to/send username@remote:/where/to/put
scp  <filename> host:/directory
scp </path/filename> nodeX:</path> 

scp username@source:/location/to/file username@destination:/where/to/put    Between two servers

##
	
## wget command
The Linux command line lets you download files from the internet using the wget command. It works in the background without hindering other running processes.

The wget command retrieves files using HTTP, HTTPS, and FTP protocols. It can perform recursive downloads, which transfer website parts by following directory structures and links, creating local versions of the web pages.

To use it, enter the following command:

wget [option] [url]

For example, enter the following command to download the latest version of WordPress:

wget https://wordpress.org/latest.zip

##

## apt-get command


apt-get is a command line tool for handling Advanced Package Tool (APT) libraries in Linux. It lets you retrieve information and bundles from authenticated sources to manage, update, remove, and install software and its dependencies.

Running the apt-get command requires you to use sudo or root privileges.

Here’s the main syntax:

apt-get [options] (command)

These are the most common commands you can add to apt-get:

**update** synchronizes the package files from their sources.
**upgrade** installs the latest version of all installed packages.
**check** updates the package cache and checks broken dependencies.

##
##

	
