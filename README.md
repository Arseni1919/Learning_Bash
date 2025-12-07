# Learning Bash

## Table of Contents

- [Intro](#intro)
- [Basic Commands](#basic-commands)
- [Text Processing](#text-processing)
- [System Monitoring](#system-monitoring)
- [Networking](#networking)
- [File Compression](#file-compression)
- [File Permissions](#file-permissions)
- [Scripting](#scripting)
- [Credits](#credits)

## Intro 

To check the version:
```bash
bash --version
```

First file: 
```txt
 #!/bin/bash
echo "Hello, Bash!"
```

To run it, do:
```bash
bash hello.sh
```

## Basic Commands

- `ls` - List directory contents
- `cd` - Change the current directory
- `pwd` - Print the current working directory
- `echo` - Display a line of text
- `cat` - Concatenate and display files
- `cp` - Copy files and directories
- `mv` - Move or rename files
- `rm` - Delete files or folders
- `touch` - Create an empty file or update its time
- `mkdir` - Create a new folder

### `ls`

The ls command has a variety of options to customize its output:

- `-l` - Long listing format `ls -l`
- `-a` - Include hidden files `ls -a`
- `-h` - Human-readable sizes (of data - like GB, MB, etc.) `ls -lh`
- `-t` - Sort by modification time
- `-r` - Reverse order while sorting
- `-R` - List subdirectories recursively
- `-S` - Sort by file size
- `-1` - List one file per line
- `-d` - List directories themselves, not their contents. An example: `ls -d */`
- `-F` - Append indicator (one of */=@|) to entries

I can also combine: `ls -la`


### `cd`

The `cd` command supports several useful options for navigating directories:

`cd ..`: Move up one directory level
`cd ~`: Change to the home directory
`cd -`: Switch to the previous directory
`cd /`: Change to the root directory

I can combine commands:

```bash
cd my_directory && ls
```

### `pwd`
The `pwd` command supports a few options to customize its output:

- `-L`: Display the logical current working directory
- `-P`: Display the physical current working directory (without symbolic links)

### `echo`

The echo command has several options to customize its output:

- `-n` - Don't add a new line at the end
- `-e` - Allow special characters like `\n` for new lines
- `-E` - Don't allow special characters (default)

### `cat`


The `cat` command is used to show the content of files in the terminal.

You can also use it to combine multiple files into one. 


### `cat`

The cat command has options to change how it shows text:

- `-n` - Add numbers to each line
- `-b` - Add numbers only to lines with text
- `-s` - Remove extra empty lines
- `-v` - Show non-printing characters (except for tabs and end of line)

The cat command is often used with piping to send the content of files to other commands.

This is useful for processing text data.

```bash
cat my_file.txt | grep "shells"
```


#### `cp`

The `cp` command is used to copy files and directories from one location to another

It's like making a duplicate of your file or folder.


The `cp` command has options to change how it works:

- `-r` - Copy all files and folders inside a directory
- `-i` - Ask before replacing files
- `-u` - Copy only if the source is newer
- `-v` - Verbose mode, show files being copied


Wildcards allow you to copy multiple files at once. For example, `cp *.txt /destination/` will copy all text files to the destination folder.

### `mv`

To move a file, use `mv source_file destination_directory`

To rename a file, use `mv old_name new_name`


The `mv` command has several options to customize its behavior:

- `-i` - Ask before replacing files
- `-u` - Move only if the source is newer
- `-v` - Verbose mode, show files being moved


Wildcards allow you to move multiple files at once. For example, `mv *.txt /destination/` will move all text files to the destination folder.

### `rm`


```bash
rm my_file.txt
```

The rm command has options to change how it works:

- `-r` - Delete a folder and everything inside it
- `-i` - Ask before deleting each file
- `-f` - Force delete without asking
- `-v` - Verbose mode, show files being removed


### `touch`

```bash
touch file.txt
```

The touch command has options to change how it works:

- `-a` - Update only when the file was last read
- `-m` - Update only when the file was last changed
- `-t` - Set the timestamp to a specific time
- `-c` - Do not create any files


### `mkdir`

```bash 
mkdir new_directory 
```


The `mkdir` command has several options to customize its behavior:

- `-p` - Create parent directories as needed
- `-v` - Show a message for each created directory
- `-m` - Set file mode (permissions)


### `man`


The `man` command is used to display the user manual of any command that can be run on the terminal.

It's a valuable resource for understanding command usage, options, and examples.

The basic syntax of the `man` command is:

Example: Man Command Syntax
```bash
man [command]
```

### `alias`

To create an alias, use the syntax `alias name='command'`, where name is the shortcut you want to use, and command is the full command you want to run.
:w
To view all current aliases, use the `alias` command without arguments.

To remove an alias, use `unalias` name.

```bash
alias ll='ls -la'
alias gs='git status'
alias
alias ll='ls -l'
alias gs='git status'
unalias gs
```

To make an alias permanent, add it to your `~/.bashrc` or `~/.bash_profile` file.

Example: Adding Permanent Alias - Open Editor
```bash
nano ~/.bashrc
```
Example: Adding Permanent Alias - Add Alias
```bash
alias ll='ls -la'
```
Example: Adding Permanent Alias - Save and Apply
```bash
source ~/.bashrc
```

### `type`

This is the most useful command because it tells you what the command is (alias, function, or file) and 
displays the code if it is a function.

```bash
type -a function_name
```

If you already know it is a function, this command prints only the source code of that function, often formatted nicely.

```bash
declare -f function_name
```


## Text Processing


### `grep` 


To search for a pattern in a file, use `grep 'pattern' filename`

The `grep` command has options to change how it works:

- `-i` - Search ignoring case differences (uppercase or lowercase)
- `-r` - Search through all files in a directory and its subdirectories
- `-v` - Find lines that do not match the pattern


Examples:

```bash
grep -i 'shell' file.txt
# Understanding Shells
#A shell is a text-based interface that lets you talk to your computer.
# There are different types of shells. Bash (Bourne Again SHell)
```


```bash
grep -r 'search_term' /home/user/my_directory
```

```bash
grep -v 'shell' my_file.txt
# Understanding Shells
```



Regular expressions allow you to search for complex patterns.

For example, `grep '^[A-Za-z]' file.txt` finds lines starting with a letter.



### `awk`


The `awk` command is used for pattern scanning and processing language.

It's useful for handling text files and used for data extraction and reporting.


The awk command has options to change how it works:

- `-F` - Set what separates the data fields
- `-v` - Set a variable to be used in the script
- `-f` - Use a file as the source of the awk program


Think of `awk` as "Microsoft Excel for the terminal."

It is a complete programming language designed specifically for processing text that is organized in rows and columns (like CSVs, log files, or the output of `ls -l`).

The standard structure is: `awk 'pattern { action }'` file

- Pattern: "Only do this if..." (e.g., if line number is > 1)
- Action: "Then do this..." (e.g., print the first word)


```bash 
awk -F"," '{print $1}' example_data.csv
```

```bash
awk -v var="Amount:" '{print var, $3}' example_data.csv
```

Awk can perform complex data manipulation tasks.

For example, `awk '{sum += $3} END {print sum}' example_data.csv` calculates the sum of the Amount column.


```bash 
awk -F"," '{sum += $3} END {print sum}' example_data.csv
```


### `sed`


The `sed` command is a stream editor used to perform basic text transformations on an input stream (a file or input from a pipeline).

It's a powerful tool for making quick edits to files or streams of data.

The `sed` command has options to change how it works:

- `-i` - Edit files directly without needing to save separately
- `-e` - Add the script to the commands to be executed
- `-n` - Don't automatically print lines
- `-r` - Use extended regular expressions
- `-f` - Add script from a file
- `-l` - Specify line length for l command


### `cat`

The `cut` command is used to remove sections from each line of files.

It's a useful tool for extracting specific fields of data from a file or output stream.

The `cut` command has options to change how it works:

- `-d` - Choose what separates the fields
- `-f` - Select specific fields to display
- `--complement` - Show all fields except the selected ones

```bash
cut -d',' -f1 example_data.txt
```

```bash
cut -f1-2 example_data.txt
```

```bash
cut --complement -f1 example_data.txt
```

```bash
cut -d' ' -f2-3 example_data.txt
```


### `sort`

The `sort` command is used to sort lines of text files.

It's a handy tool for organizing data in files.


The `sort` command has options to change how it works:

- `-r` - Sort in reverse order
- `-n` - Sort numbers correctly. Without this option, numbers are sorted lexicographically, meaning "10" would come before "2".
- `-k` - Sort by a specific column
- `-u` - Remove duplicate lines
- `-t` - Specify a delimiter for fields


The `-k2,2` means that the sorting columns start at 2 and finish at 2.


```bash
sort fruits.txt
sort -r fruits.txt
sort -t "," -k2,2 fruits.txt
sort -t "," -n -k2,2 fruits.txt
sort -u fruits.txt
sort -t "," -k1,1 -k2,2r fruits.txt
```

`sort -t "," -k1,1 -k2,2r fruits.txt` sorts by the first column, and then by the second column in reverse order.



### `tail`


The `tail` command is used to display the last part of files.

It's particularly useful for viewing the end of log files or any file that is being updated in real-time.


The basic syntax of the `tail` command is:

```bash
tail [OPTION]... [FILE]...
```

The `tail` command has several options to customize its behavior:

- `-n [number]`: Display the last [number] lines of the file.
- `-f`: Follow the file as it grows, useful for monitoring log files.
- `-c [number]`: Display the last [number] bytes of the file.
- `--pid=[pid]`: Terminate after the process with the given PID dies.
- `--retry`: Keep trying to open a file even if it is inaccessible.

By default, `tail` shows the last 10 lines.


```bash
tail -n 5 logfile.txt
tail -f logfile.txt
tail -c 20 logfile.txt
tail -f --pid=1234 logfile.txt
tail --retry -f logfile.txt
```

Common scenarios where the `tail` command is beneficial include:

Monitoring server logs to detect issues in real-time.
Checking the latest entries in a continuously updated file.
Debugging applications by reviewing recent log entries.


### `head`


The `head` command is used to display the first part of files.

It's particularly useful for previewing the start of a file to understand its structure.


The `head` command displays the first 10 lines of a file by default.


The head command has several options used to customize its behavior:

- `-n [number]`: Display the first `[number]` lines of the file.
- `-c [number]`: Display the first `[number]` bytes of the file.

The `-q` option suppresses the printing of headers when multiple files are being processed. This is useful when you want to view the contents of multiple files without the file names being printed.

```bash
head logfile.txt
head -n 5 logfile.txt
head -c 20 logfile.txt
head -n 3 logfile.txt logfile2.txt
head -q -n 3 logfile.txt logfile2.text
```

The `head` command is commonly used to:

Preview the start of a file to understand its structure.
Quickly check the contents of a file without opening it fully.
Extract the header information from a data file.


## System Monitoring

### `ps`

The `ps` command is used to report a snapshot of current processes.

It's a useful tool for monitoring and managing processes on your system.

All examples below use a hypothetical process list for demonstration:

```bash
PID TTY          TIME CMD
1234 pts/0    00:00:01 bash
5678 pts/1    00:00:02 python
9101 pts/2    00:00:03 node
```

The `ps` command output consists of several columns, each representing different aspects of the system's processes:

- `PID`: Process ID, a unique identifier for each process.
- `TTY`: Terminal type associated with the process.
- `TIME`: Total CPU time used by the process.
- `CMD`: The command that started the process.


The `ps` command has options to change how it works:

- `-e` - Show all processes
- `-f` - Show detailed information
- `-u` - Show processes for a specific user
- `-a` - Show all processes with a terminal
- `-x` - Show processes without a terminal



```bash
ps
ps -e
ps -f
ps -a
ps -x
ps -u user
ps -ef
```

### `top`


The `top` command output consists of several columns, each representing different aspects of the system's processes:

- `PID`: Process ID, a unique identifier for each process.
- `USER`: The user account that owns the process.
- `PR`: Priority of the process.
- `NI`: Nice value, which affects scheduling priority.
- `VIRT`: Virtual memory size used by the process.
- `RES`: Resident memory size, the non-swapped physical memory the process uses.
- `SHR`: Shared memory size.
- `S`: Process status (e.g., S for sleeping, R for running).
- `%CPU`: CPU usage percentage.
- `%MEM`: Memory usage percentage.
- `TIME+`: Total CPU time the process has used since it started.
- `COMMAND`: The command that started the process.

The `top` command has options to change how it works:

- `-d` - Set the time between updates
- `-p` - Monitor specific PIDs
- `-u` - Show tasks for a specific user
- `-n` - Set the number of iterations
- `-b` - Batch mode operation

The `-b` option allows top to run in batch mode, suitable for sending output to other programs or files.



```bash
top
top -d 5
top -p 1234
top -u user
top -n 2
top -b -n 1
```

On Linux (Standard)
If you were on Linux, top often defaults to KB. You can toggle "Human Readable" scaling while it is running by pressing:

- `e`: Changes the units for the rows (processes) -> MB, GB, TB, PB.

- `E`: Changes the units for the header (summary) -> MB, GB, TB, PB.


### `df`

The `df` command is used to report file system disk space usage.

It's a useful tool for checking available storage on your system.

All examples below use a hypothetical output for demonstration:

```bash
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       20480000 1024000  19456000   5% /
tmpfs            4096000       0   4096000   0% /dev/shm
/dev/sdb1       10240000  512000   9728000   5% /mnt/data
```

- `Filesystem`: The name of the file system.
- `1K-blocks`: Total size of the file system in 1K blocks.
- `Used`: Amount of space used.
- `Available`: Amount of space available for use.
- `Use%`: Percentage of space used.
- `Mounted on`: Directory where the file system is mounted.



The `df` command has options to change how it works:

- `-h` - Show sizes in human-readable format (e.g., KB, MB)
- `-a` - Show all file systems, even empty ones
- `-T` - Show the type of file system
- `-i` - Show inode usage
- `-P` - Use POSIX output format


The `-i` option allows you to show `inode` usage.

**POSIX**: POSIX (Portable Operating System Interface) is a set of standards specified by the IEEE for maintaining compatibility between operating systems.



```bash
df
df -h
df -a
df -T
df -i
df -hT
```

### `du`


The `du` command is used to estimate file space usage.

It's helpful for finding out how much space files and directories take up.

All examples below use a hypothetical output for demonstration:

```bash
8.0K    ./dir1
12K     ./dir2
20K     .
```

The `du` command output consists of two columns:

- `Size`: The amount of disk space used by the file or directory.
- `Path`: The file or directory path.


The `du` command has options to change how it works:

- `-h` - Show sizes in human-readable format (e.g., KB, MB)
- `-s` - Show only the total size for each item
- `-a` - Show sizes for all files, not just directories
- `-c` - Produce a grand total
- `--mx-depth=N` - Limit the depth of directory traversal


```bash 
du 
du -h
du -s
du -a
du -c
du --max-depth=1
du -h --max-depth=1

```

### `free`


The `free` command is used to display the amount of free and used memory in the system.

It's useful for monitoring memory usage and managing system resources.

The `free` command has options to change how it works:

- `-h` - Show memory in human-readable format (e.g., KB, MB, GB)
- `-b` - Show memory in bytes
- `-k` - Show memory in kilobytes (KB)
- `-m` - Show memory in megabytes (MB)
- `-g` - Show memory in gigabytes (GB)
- `-s [interval]` - Continuously display memory usage at specified intervals
- `-t` - Display total memory

```bash
free -b
free -s 5
...
```


### `kill`

The `kill` command is used to terminate processes in a Unix-like operating system.

It's a powerful tool for managing system resources and ensuring that processes do not consume more resources than necessary.

The `kill` command is commonly used to:

- Terminate unresponsive processes.
- Manage system resources by stopping unnecessary processes.
- Send specific signals to processes for custom handling.


The `kill` command has several options to customize its behavior:

- `-9`: Forcefully terminate a process.
- `-l`: List all signal names.
- `-s [signal]`: Specify a signal to send.
- `-p`: Print the process ID.

Despite the name, the `kill` command isn't just for killing. It is actually a signal sender. It sends a specific code to a process, and the process decides how to react to it.We have "so many" signals because stopping a program is not a binary action. Sometimes you want it to save its work first; other times you want to freeze it; other times you want to obliterate it immediately because it's crashed.Here is the breakdown of the ones you actually need to know.

Here are the three most important kill signals in bullet points:

- Signal `-15` (SIGTERM) – "The Polite Request" This is the default signal. It asks the program to stop nicely. The program is allowed to "catch" this signal, meaning it can finish its current task, save open files, and close connections before exiting. However, because it is polite, a frozen or buggy program might ignore it.

- Signal `-9` (SIGKILL) – "The Sniper Shot" This is the forceful kill. It bypasses the application entirely and tells the Operating System kernel to rip the process out of memory immediately. The program gets zero warning and cannot save any data. It cannot be ignored, blocked, or handled by the program. You should only use this if SIGTERM fails.

- Signal `-2` (SIGINT) – "The Ctrl+C" This is the "Interrupt" signal. It is exactly what is sent when you press Ctrl+C on your keyboard while a script is running. It functions very similarly to SIGTERM (it asks the program to stop), but it is specifically designed to be triggered by the user interface/terminal.



```bash
kill -9 1234
kill -l
kill -s SIGTERM 1234
kill -p 1234
```



### `uptime`

The `uptime` command is used to find out how long the system has been running.

It provides a quick overview of the system's performance, including:


- `Current Time`: The time at which the command was run.
- `Uptime Duration`: How long the system has been running since the last reboot.
- `Number of Users`: The number of users currently logged into the system.
- `Load Averages`: The system load averages for the past 1, 5, and 15 minutes.


The load averages provide a snapshot of the system's workload:

- A lower load average indicates a less busy system.
- A higher load average suggests the system is busier.
- Load averages above 1.0 per core may indicate the system is overloaded.


```bash
uptime
```


## Networking


### `ping`


The `ping` command is used to send ICMP ECHO_REQUEST to network hosts.

It's a useful tool for checking network connectivity and diagnosing network issues.


The `ping` command has options to change how it works:

- `-c` - Send a specific number of ping requests. This is useful for limiting the number of packets sent.
- `-i` - Wait a specific number of seconds between sending each packet. This can be useful for reducing network traffic when using ping.
- `-t` - Set the IP Time to Live (TTL). This determines the maximum number of hops a packet can take before being discarded.
- `-q` - Quiet output, only show summary. This is useful for scripts or when you only need the final statistics.
- `-s` - Specify the number of data bytes to be sent. This can be useful for testing network performance with different packet sizes.


The output of the `ping` command provides several key pieces of information:

- `Bytes`: The size of the ICMP packet sent
- `Time`: The round-trip time it took for the packet to reach the host and return, measured in milliseconds
- `TTL (Time to Live)`: The remaining lifespan of the packet, which decreases by one for each hop
- `Packet Loss`: The percentage of packets that were lost during transmission
- `Round-Trip Time Statistics`: Includes minimum, average, maximum, and standard deviation of the round-trip times


```bash
ping google.com
ping -c 4 google.com
ping -i 2 google.com
ping -t 64 google.com
ping -c 4 -q google.com

```



### `curl`


The `curl` command is used to transfer data from or to a server using various protocols like HTTP, HTTPS, FTP, and more.

It's a versatile tool for downloading files, testing APIs, and more.


The `curl` command has options to change how it works:

- `-O` - Save the file with the same name as the remote file. This is useful for downloading files directly to your local system with their original names.
- `-L` - Follow redirects. This is useful when accessing URLs that may redirect to another location.
- `-I` - Fetch the HTTP headers only. This is useful for checking server response headers without downloading the entire content.
- `-d` - Send data with POST request. This is useful for submitting form data or interacting with APIs.
- `-u` - Specify user and password for server authentication. This is useful for accessing protected resources.


```bash
curl http://example.com/file.txt
curl -O http://example.com/file.txt
curl -L http://example.com/redirect
curl -I http://example.com
curl -d "fname=John" https://www.example.com/action_page.php
curl -u user:password http://example.com/protected
```


### `wget`



The `wget` command is used to download files from the web.

It's a powerful tool for downloading single files, entire websites, or even batch downloads.


The `wget` command has options to change how it works:

- `-b` - Run in the background. This is useful for long downloads that you don't want to monitor continuously.
- `-q` - Quiet mode (no output). This is useful for scripts or automated tasks where output is not needed.
- `-r` - Download directories recursively. This is useful for downloading entire websites or directories.
- `-c` - Continue getting a partially-downloaded file. The -c option allows you to continue downloading a file that was partially downloaded. This is useful for resuming interrupted downloads.
- `--lmit-rate` - Limit download speed. This is useful for managing bandwidth usage.


```bash 
wget http://example.com/file.txt
wget -b http://example.com/file.txt
wget -q http://example.com/file.txt
wget -r http://example.com/directory/
wget -c http://example.com/largefile.zip
wget --limit-rate=200k http://example.com/file.txt
```


### `ssh`


The `ssh` command is used to connect to a remote machine securely.

To connect to a remote host, use `ssh user@hostname`.

Here are some common options you can use with the `ssh` command:

- `-p` - Specify the port. By default, SSH uses port 22.
- `-i` - Use a private key file. This is useful when you have a specific key for a server.
- `-v` - Enable verbose mode. This is helpful for debugging.
- `-C` - Enable compression. The -C option enables compression, which can speed up data transfer by reducing the amount of data sent over the network.
- `-X` - Enable X11 forwarding. The -X option allows X11 forwarding, enabling you to run graphical applications on the remote server and display them locally.
- `-o` - Specify options directly on the command line. This is useful for overriding configuration settings.


```bash
ssh user@example.com
ssh -p 2222 user@example.com
ssh -i /path/to/private_key user@example.com
ssh -v user@example.com
ssh -C user@example.com
ssh -X user@example.com
ssh -o StrictHostKeyChecking=no user@example.com
```


### `scp`


The `scp` command is used to securely copy files between hosts on a network.

The `scp` command supports various options to customize its behavior:

- `-r` - Recursively copy entire directories
- `-P` - Specify the port to connect to on the remote host. By default, SCP uses port 22.
- `-i` - Specify an identity (private key) file
- `-C` - Enable compression
- `-v` - Enable verbose mode
- `-l` - Limit the bandwidth used by the copy


```bash
scp file.txt user@example.com:/home/user/
...
```

- `cp` (Copy) is for moving files inside the same computer.
- `scp` (Secure Copy) is for moving files between two different computers over the internet (or local network).




### `rsync`


The `rsync` command is used to efficiently transfer and synchronize files across computer systems, by checking the timestamp and size of files.

Here are some common options you can use with the `rsync` command:

- `-a` - Archive mode
- `-v` - Increase verbosity
- `-z` - Compress file data
- `--delete` - Delete extraneous files
- `-r` - Recurse into directories
- `-u` - Skip files that are newer on the receiver
- `--progress` - Show progress during transfer

Here are the 4 main reasons we need it:

1. The "Delta" Algorithm (Speed)

This is the #1 reason. If you have a 10 GB file and you modify just 1 KB of it:

cp / scp: Will copy the entire 10 GB again.

rsync: Will compare the two files, detect the difference, and send only the 1 KB change.

This saves massive amounts of bandwidth and time, especially over slow networks.

2. It Can Resume (Resilience)

If you are transferring a large file (e.g., 50GB of logs) and your internet cuts out at 90%:

cp / scp: You have to start over from 0%.

rsync: You run the command again, and it looks at what is already there and finishes the remaining 10%.

3. True Mirroring (Synchronization)

rsync ensures the destination folder looks exactly like the source folder.

It preserves permissions, ownership, and timestamps (using the -a flag).

It can delete files at the destination if they were deleted at the source (using the --delete flag). cp cannot do this.

4. It works over SSH

rsync is built to work securely over the network. It uses SSH by default for encryption, so it is just as secure as scp, but smarter.


```bash
rsync -avz --progress source_folder/ destination_folder/
```


## File Compression

### `zip`

The `zip` command is used to package and compress files into a ZIP archive.

Here are some common options you can use with the zip command:

- `-r` - Recursively zip directories
- `-u` - Update files in the archive if they are newer
- `-d` - Delete files from the archive
- `-e` - Encrypt the contents of the ZIP archive
- `-x` - Exclude specific files from being zipped

```bash
zip archive.zip file1 file2
```


### `unzip`


The `unzip` command is used to extract compressed files from a ZIP archive.

Here are some common options you can use with the unzip command:

- `-l` - List archive files
- `-t` - Test compressed archive files
- `-d` - Extract files into a different directory
- `-o` - Overwrite existing files without prompting
- `-x` - Exclude specific files from being extracted


```bash
unzip archive.zip -x file1
unzip -l archive.zip
unzip archive.zip
```


### `tar`

The `tar` command is used to create, maintain, modify, and extract files from an archive file.

The main difference is their philosophy on compression and operating system compatibility.

ZIP is a "Compress, then Archive" tool. (Windows Standard)

TAR is an "Archive, then Compress" tool. (Linux Standard)

Here are some common options you can use with the tar command:

- `-c` - Create a new archive
- `-x` - Extract files from an archive
- `-t` - List the contents of an archive
- `-z` - Filter the archive through gzip
- `-v` - Verbosely list files processed
- `-f` - Specify the filename of the archive

```bash
tar -xvf archive.tar
...
```





## File Permissions

Understanding File Permissions and Ownership

In Unix-like operating systems, file permissions and ownership are crucial for managing access to files and directories.

Each file has an owner, a group, and a set of permissions that determine who can read, write, or execute the file.

File Permissions

File permissions are represented by a series of characters that indicate the permissions for the _owner_, the _group_, and _others_. The permissions are:

- `r`: Read permission
- `w`: Write permission
- `x`: Execute permission

For example, the permission `rwxr-xr--` means the owner can read, write, and execute the file, the group can read and execute, and others can only read.


Numeric Representation of Permissions
File permissions can also be represented numerically, which is often used in scripts and command-line operations:

- `0`: No permission
- `1`: Execute permission
- `2`: Write permission
- `3`: Write and execute permissions
- `4`: Read permission
- `5`: Read and execute permissions
- `6`: Read and write permissions
- `7`: Read, write, and execute permissions

For example, the numeric permission `755` means the owner can read, write, and execute (7), and the group and others can read and execute (5).


File Ownership

Each file has an owner and a group associated with it. The owner is typically the user who created the file, and the group is a collection of users who share access to the file.

Commands like `chown` and `chgrp` are used to change the ownership and group of a file, respectively.

Common Commands

Here are some common commands for managing file permissions and ownership:

`chmod`: Change file permissions
`chown`: Change file ownership
`chgrp`: Change group ownership



### `chmod`


The `chmod` command is used to change the file permissions in Unix-like operating systems.

It allows you to set who can read, write, or execute a file.


The `chmod` command has several options to customize its behavior:

- `-R`: Change files and directories recursively.
- `-v`: Output a diagnostic for every file processed.


```bash
chmod -R 755 /path/to/directory
chmod -v 644 file.txt
```


### `chown`

The `chown` command is used to change the ownership of files and directories in Unix-like operating systems.

It allows you to set which user and group own a file.

The `chown` command has several options to customize its behavior:

- `-R`: Change files and directories recursively.
- `-v`: Output a diagnostic for every file processed.


```bash
chown -R user:group /path/to/directory
chown -v user file.txt
```

### `chgrp`


The `chgrp` command is used to change the group ownership of files and directories in Unix-like operating systems. It allows you to set which group owns a file.


The `chgrp` command has several options to customize its behavior:

- `-R`: Change files and directories recursively.
- `-v`: Output a diagnostic for every file processed.


## Scripting


- `Comments`: Comments start with a # and Bash ignores them.
- `Command Order`: Commands run one after the other, from top to bottom.
- `Semicolons`: Use ; to run multiple commands on the same line.


```bash
# This script prints a greeting message
echo "Hello, World!"
echo "This is a test"; echo "This is another test"
```


Correct bash script:

```bash
#!/bin/bash
# Assign a value to a variable
name="World"
echo "Hello, $name!"
```

### Variables

Variables in Bash are used to store data that can be used and manipulated throughout your script or command-line session. Bash variables are untyped, meaning they can hold any type of data.



```bash
name="John Doe"
echo "Hello, $name!"
number=42
echo "The number is $number"
```

Environment variables are special variables that affect the way processes run on your system. They are often used to store system-wide values like the location of executables or the default editor.

```bash
# Display the PATH environment variable
echo "Your PATH is $PATH"
```


Local variables are only available within the block of code in which they are defined, such as within a function. Global variables are accessible from anywhere in the script.


```bash
# Define a local variable in a function
my_function() {
  local local_var="I am local"
  echo $local_var
}
my_function
```


Variables can be used in various operations, such as concatenation and arithmetic.

- `Concatenation`: Combine strings using variables.
- `Arithmetic`: Perform calculations using variables.


```bash
# Concatenation
greeting="Hello, "
name="World"
echo "$greeting$name"

# Arithmetic
num1=5
num2=10
sum=$((num1 + num2))
echo "The sum is $sum"
```



### Data Types


Strings

Strings are sequences of characters used to store text. They can be manipulated using various string operations such as concatenation and substring extraction.



```bash
# String example
greeting="Hello, World!"
name="Alice"
full_greeting="$greeting, $name!"
echo $full_greeting
```

Numbers

Numbers in Bash can be used for arithmetic operations. Bash supports integer arithmetic natively, such as addition, subtraction, multiplication, and division.


```bash
# Number example
num1=5
num2=10
sum=$((num1 + num2))
difference=$((num2 - num1))
product=$((num1 * num2))
quotient=$((num2 / num1))
echo "Sum: $sum, Difference: $difference, Product: $product, Quotient: $quotient"
```


Arrays

Arrays are used to store multiple values in a single variable. Each element in an array is accessed using an index. You can iterate over arrays and modify elements.

```bash
# Array example
fruits=("apple" "banana" "cherry")
for fruit in "${fruits[@]}"; do
  echo $fruit
done
```

Associative Arrays

Associative arrays allow you to use named keys to access values. They are similar to dictionaries in other programming languages. You can add or remove keys and values.


```bash
# Associative array example
declare -A colors
colors[apple]="red"
colors[banana]="yellow"
colors[grape]="purple"
unset colors[banana]
echo ${colors[apple]} # red
echo ${colors[grape]} # purple
```

You need to declare the dict first:

```bash
declare -A colors
```

Data Type Limitations

Bash does not support floating-point arithmetic natively. For such operations, consider using external tools like `bc` or `awk`.



### Operators


Comparison Operators

- `-eq`: Equal to
- `-ne`: Not equal to
- `-lt`: Less than
- `-le`: Less than or equal to
- `-gt`: Greater than
- `-ge`: Greater than or equal to


String Comparison Operators

- `=`: Equal to
- `!=`: Not equal to
- `<`: Less than, in ASCII alphabetical order
- `>`: Greater than, in ASCII alphabetical order



Arithmetic Operators

- `+`: Addition
- `-`: Subtraction
- `*`: Multiplication
- `/`: Division
- `%`: Modulus (remainder of division)

For exponentiation, use external tools like `bc` or `awk`.

Logical Operators

- `&&`: Logical AND
- `||`: Logical OR
- `!`: Logical NOT


File Test Operators

- `-e`: Checks if a file exists
- `-d`: Checks if a directory exists
- `-f`: Checks if a file is a regular file
- `-s`: Checks if a file is not empty

These operators are used inside `if` statements (specifically inside the square brackets [ ... ]). They allow your script to make decisions based on the state of your filesystem.

```bash
if [ -e "./final_merged_logs.csv" ]; then
    echo "Found the file (or folder)!"
else
    echo "Nothing exists at this path."
fi
```

### Bash If...Else

If statements allow you to execute code based on a condition. If the condition is true, the code block will run.

The condition is enclosed in square brackets [ ] and the statement ends with fi, which is if spelled backward, marking the end of the if block.

Example: If Statement

```bash
# Basic if statement
num=15
if [ $num -gt 10 ]; then
  echo "Number is greater than 10"
fi
```


Example: If...Else Statement


```bash
# If...else statement
num=8
if [ $num -gt 10 ]; then
  echo "Number is greater than 10"
else
  echo "Number is 10 or less"
fi
```


Example: Elif Statement

```bash
# If...elif...else statement
num=10
if [ $num -gt 10 ]; then
  echo "Number is greater than 10"
elif [ $num -eq 10 ]; then
  echo "Number is exactly 10"
else
  echo "Number is less than 10"
fi
```


Example: Nested If Statement

```bash
# Nested if statement
num=5
if [ $num -gt 0 ]; then
  if [ $num -lt 10 ]; then
    echo "Number is between 1 and 9"
  fi
fi
```


### Bash Loops


Example: For Loop


```bash
# For loop example
for i in {1..5}; do
  echo "Iteration $i"
done
```


Example: While Loop


```bash
# While loop example
count=1
while [ $count -le 5 ]; do
  echo "Count is $count"
  ((count++))
done
```

Example: Until Loop


Until loops are similar to while loops, but they execute until a specified condition becomes true.


```bash
# Until loop example
count=1
until [ $count -gt 5 ]; do
  echo "Count is $count"
  ((count++))
done
```

Example: Break and Continue

Break and continue statements are used to control loop execution. break exits the loop, while continue skips to the next iteration.


```bash
# Break and continue example
for i in {1..5}; do
  if [ $i -eq 3 ]; then
    continue
  fi
  echo "Number $i"
  if [ $i -eq 4 ]; then
    break
  fi
done
```


Example: Nested Loops

Nested loops allow you to place one loop inside another, enabling more complex iteration patterns.

```bash
# Nested loops example
for i in {1..3}; do
  for j in {1..2}; do
    echo "Outer loop $i, Inner loop $j"
  done
done
```




### Bash functions


Example: Define a Function

```bash
my_function() {
  echo "Hello, World!"
}
```


Calling Functions

In Bash, execute (or call) a function by using its name.
Functions can be called multiple times, which helps in reusing code:

```bash
my_function
```

Advanced Function Features

Functions can accept arguments, return values, and use local variables. Here's an example of a function that takes an argument and uses a local variable:

```bash
greet() {
  local name=$1
  echo "Hello, $name!"
}
greet "Alice"
```

You can also return values from functions using `echo` or the `return` statement:

```bash
add() {
  local sum=$(($1 + $2))
  echo $sum
}
result=$(add 5 3)
echo "The sum is $result"
```



### Bash Arrays

Example: Create an Array


```bash
my_array=("value1" "value2" "value3")
```

To access elements in a Bash array, use the index of the element.

The index is specified in square brackets:


```bash
echo ${my_array[0]}
```


Example: Modify Array Elements

```bash
my_array[1]="new_value"
```


### `cron`


The `cron` system is a time-based job scheduler in Unix-like operating systems.

It automates the execution of tasks (known as cron jobs) at specified intervals.

While `cron` is the background service that runs these tasks, `crontab` is the command used to manage them.

There is no direct "cron" command; instead, you use `crontab` to set up and control cron jobs.


The crontab command allows you to define scheduled tasks.

> These tasks are specified in a crontab file, which is a simple text file containing a list of commands meant to be run at specified times.

The basic syntax of the crontab command is:

`crontab [options]`

Options
- `-e`: Edit the crontab file for the current user.
- `-l`: List the crontab entries for the current user.
- `-r`: Remove the crontab file for the current user.


Setting Up Cron Jobs

Cron jobs are defined using a specific syntax in the crontab file. Each line in the file represents a task and follows this format:

```crontab
* * * * * command_to_execute
```


- Minute: 0-59
- Hour: 0-23
- Day of Month: 1-31
- Month: 1-12
- Day of Week: 0-7 (0 and 7 are Sunday)

Each asterisk can be replaced with a specific value or range to schedule the command at specific times.

Example: Schedule a Task

To run a script every day at midnight, you would use:

```crontab
0 0 * * * /path/to/script.sh
```

This entry will execute /path/to/script.sh every day at 00:00 (midnight).

Common Uses

Cron jobs are commonly used to:

- Automate system maintenance tasks, like backups and updates.
- Schedule scripts to run at specific times or intervals.
- Perform regular monitoring and reporting tasks.




## Credits

- [w3school | Bash Tutorial](https://www.w3schools.com/bash/index.php)
