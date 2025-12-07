# Learning Bash

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


## File Compression


## File Permissions


## Scripting




## Credits

- [w3school | Bash Tutorial](https://www.w3schools.com/bash/index.php)
