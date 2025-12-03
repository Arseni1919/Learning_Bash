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








## Credits

- [w3school | Bash Tutorial](https://www.w3schools.com/bash/index.php)
