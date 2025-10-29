
# how do i exacute a bash file

There are several ways to execute a bash script file in Linux. Here are the most common methods:

## Method 1: Using the bash Command

The simplest way is to use the `bash` command followed by your script name:

```bash
bash script.sh
```

This works regardless of file permissions and doesn't require the script to be executable.[^1][^2][^4]

## Method 2: Using the sh Command

You can also use the `sh` command:

```bash
sh script.sh
```

This runs the script through the system's default shell interpreter.[^2][^4]

## Method 3: Make the Script Executable (Most Common)

This is the most versatile method. First, make the script executable using `chmod`:

```bash
chmod +x script.sh
```

Then run it directly:

```bash
./script.sh
```

The `./` tells the system to look in the current directory for the script.[^4][^1][^2]

## Method 4: Using source Command

The `source` command executes the script in the current shell environment:

```bash
source script.sh
```

Or alternatively:

```bash
. script.sh
```


## Important Notes

**Shebang Line**: Your bash script should start with a shebang line to specify the interpreter:

```bash
#!/bin/bash
```

This tells the system to use the bash shell to execute the script.[^5][^4]

**File Permissions**: If you get a "Permission denied" error, you need to make the script executable using `chmod +x` as shown in Method 3.[^1][^2]

**Path Considerations**: If your script isn't in the current directory, specify the full path:

```bash
/path/to/your/script.sh
```

Or use relative paths as needed.[^2][^1]

The most common and recommended approach is Method 3 (making the script executable and running with `./script.sh`) as it's the most portable and follows standard Linux conventions.[^4][^2]
<span style="display:none">[^3][^6]</span>

<div align="center">⁂</div>

[^1]: https://stackoverflow.com/questions/2177932/how-do-i-execute-a-bash-script-in-terminal

[^2]: https://phoenixnap.com/kb/run-bash-script

[^3]: https://itsfoss.community/t/running-a-bash-script/9621

[^4]: https://www.geeksforgeeks.org/linux-unix/how-to-run-bash-script-in-linux/

[^5]: https://www.freecodecamp.org/news/bash-scripting-tutorial-linux-shell-script-and-command-line-for-beginners/

[^6]: https://www.youtube.com/watch?v=cgVbqxtx3hU

