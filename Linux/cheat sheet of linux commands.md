#linux #linuxcommands
## File and Directory Operations

| Command | Description |
| :-- | :-- |
| `ls` | List directory contents |
| `ls -la` | List with details including hidden files |
| `pwd` | Show current directory path |
| `cd <directory>` | Change directory |
| `cd ..` | Move up one directory level |
| `cd ~` | Go to home directory |
| `mkdir <name>` | Create directory |
| `rmdir <name>` | Remove empty directory |
| `rm <file>` | Delete file |
| `rm -rf <directory>` | Recursively delete directory and contents |
| `cp <source> <dest>` | Copy file |
| `cp -r <source> <dest>` | Copy directory recursively |
| `mv <source> <dest>` | Move/rename file or directory |
| `touch <filename>` | Create empty file or update timestamp |

## File Viewing and Editing

| Command | Description |
| :-- | :-- |
| `cat <file>` | Display file contents |
| `less <file>` | View file with navigation |
| `head <file>` | Show first 10 lines |
| `head -n 20 <file>` | Show first 20 lines |
| `tail <file>` | Show last 10 lines |
| `tail -f <file>` | Follow file changes in real-time |
| `grep <pattern> <file>` | Search for pattern in file |
| `find <path> -name <pattern>` | Find files by name |
| `wc <file>` | Count lines, words, characters |

## File Permissions

| Command | Description |
| :-- | :-- |
| `chmod 755 <file>` | Set file permissions (rwxr-xr-x) |
| `chmod +x <file>` | Make file executable |
| `chown <user>:<group> <file>` | Change file ownership |
| `sudo <command>` | Execute command with superuser privileges |

## Process Management

| Command | Description |
| :-- | :-- |
| `ps aux` | Show running processes |
| `top` | Display running processes (real-time) |
| `htop` | Enhanced process viewer |
| `kill <pid>` | Terminate process by ID |
| `killall <name>` | Kill processes by name |
| `jobs` | List active jobs |
| `bg` | Send job to background |
| `fg` | Bring job to foreground |
| `nohup <command> &` | Run command immune to hangups |

## System Information

| Command | Description |
| :-- | :-- |
| `uname -a` | System information |
| `whoami` | Current username |
| `id` | User and group IDs |
| `uptime` | System uptime and load |
| `df -h` | Disk space usage |
| `du -sh <directory>` | Directory size |
| `free -h` | Memory usage |
| `lscpu` | CPU information |
| `lsblk` | List block devices |

## Network Commands

| Command | Description |
| :-- | :-- |
| `ping <host>` | Test network connectivity |
| `wget <url>` | Download file from web |
| `curl <url>` | Transfer data from/to server |
| `ssh <user>@<host>` | Secure shell connection |
| `scp <file> <user>@<host>:<path>` | Secure copy over network |
| `netstat -tuln` | Show network connections |
| `ip addr` | Show IP addresses |

## Archive and Compression

| Command | Description |
| :-- | :-- |
| `tar -czf archive.tar.gz <files>` | Create compressed archive |
| `tar -xzf archive.tar.gz` | Extract compressed archive |
| `zip archive.zip <files>` | Create ZIP archive |
| `unzip archive.zip` | Extract ZIP archive |

## Text Processing

| Command | Description |
| :-- | :-- |
| `sort <file>` | Sort lines in file |
| `uniq <file>` | Remove duplicate lines |
| `cut -d',' -f1 <file>` | Extract columns from CSV |
| `awk '{print $1}' <file>` | Print first column |
| `sed 's/old/new/g' <file>` | Replace text in file |

## System Control

| Command | Description |
| :-- | :-- |
| `systemctl status <service>` | Check service status |
| `systemctl start <service>` | Start service |
| `systemctl stop <service>` | Stop service |
| `systemctl restart <service>` | Restart service |
| `history` | Show command history |
| `clear` | Clear terminal screen |
| `man <command>` | Show manual page for command |

## Useful Shortcuts

| Shortcut | Description |
| :-- | :-- |
| `Ctrl+C` | Cancel current command |
| `Ctrl+Z` | Suspend current command |
| `Ctrl+D` | Exit current shell |
| `Ctrl+L` | Clear screen |
| `Ctrl+R` | Search command history |
| `Tab` | Auto-complete |
| `!!` | Repeat last command |
