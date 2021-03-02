---
Title: redirecting streams
Description:
Date: 2021-03-02 18:18
References:
Tags: #linux
---

# Redirecting streams

## Basic command output redirection
```bash

# redirect command output to file. Removes file if it exists. Creates file if it does not exist. Either way, it starts from a clean empty file. 
command > file

# redirect command output to file, but append the output.
command >> file

# Channel a file to the standard input from the command
command < file
```

## stdin, stdout and stderr (default streams)

- **stdin**: Stands for standard input. It takes text as input
- **stdout**: Stands for standard output. The text output of a command is stored in stdout stream.
- **stderr**: Stands for standard error. Whenever a command faces an error the error message is stored in this stream. 


| streamId | name   |
| -------- | ------ |
| 0        | stdin  |
| 1        | stdout |
| 2        | stderr |

### common redirections

** in bash `&>`  has the same meaning as `2>&1` **

```bash
	# redirect stderr to stdout and have error messages sent to the same file as standard output.
	command > file 2>&1
	
	# Another way to redirect stderr to stdout using '&>'.
	command &> file
	
	# redirect std-err to /dev/null. Instead of printing the errors.
	command 2>/dev/null
```

