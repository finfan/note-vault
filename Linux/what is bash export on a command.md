<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# what is bash export on a command

The bash `export` command is a built-in shell command that makes variables and functions available to child processes by marking them for inclusion in the environment of subsequently executed commands.[^1][^4]

## Basic Function

The `export` command promotes shell variables to environment variables, allowing them to be inherited by child processes. Without `export`, variables are only available in the current shell session.[^6]

## Syntax

```bash
export [-f] [-n] [name[=value] ...] 
export -p
```


## Common Usage Examples

**Export an existing variable:**

```bash
MY_VAR="hello world"
export MY_VAR
```

**Set and export in one command:**

```bash
export MY_VAR="hello world"
```

**Export PATH variable (most common use):**

```bash
export PATH=$PATH:/usr/local/bin
```

This adds `/usr/local/bin` to the existing PATH variable.[^6]

## Key Options

**`-p` option:** Lists all exported variables in the current shell

```bash
export -p
```

**`-f` option:** Exports functions instead of variables

```bash
my_function() { echo "Hello"; }
export -f my_function
```

**`-n` option:** Removes variables from the export list

```bash
export -n MY_VAR
```


## Practical Example

Here's a demonstration of how `export` works with child processes:

```bash
# Without export
VAR="test"
bash           # Start new shell
echo $VAR      # Empty - variable not inherited

# With export  
VAR="test"
export VAR
bash           # Start new shell
echo $VAR      # Outputs "test" - variable inherited
```

The `export` command is essential for setting environment variables that need to be available to scripts, applications, and child processes spawned from your current shell session.[^3][^4][^1]
<span style="display:none">[^2][^5]</span>

<div align="center">⁂</div>

[^1]: https://www.digitalocean.com/community/tutorials/export-command-linux

[^2]: https://stackoverflow.com/questions/13795237/what-does-the-export-command-do

[^3]: https://phoenixnap.com/kb/linux-export-command

[^4]: https://www.geeksforgeeks.org/linux-unix/export-command-in-linux-with-examples/

[^5]: https://www.baeldung.com/linux/bash-set-and-export

[^6]: https://linuxconfig.org/learning-linux-commands-export

