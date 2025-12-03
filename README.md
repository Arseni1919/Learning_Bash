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



## Credits

- [w3school | Bash Tutorial](https://www.w3schools.com/bash/index.php)
