
#linux #filetransfer #rsync

# rsync(1) - Linux Manual Page

  

## NAME
rsync - a fast, versatile, remote (and local) file-copying tool[^3][^5]
## SYNOPSIS
**Local:**

```

rsync [OPTION...] SRC... [DEST]

```
**Access via remote shell:**

```

Pull: rsync [OPTION...] [USER@]HOST:SRC... [DEST]

Push: rsync [OPTION...] SRC... [USER@]HOST:DEST

```

**Access via rsync daemon:**
```

Pull: rsync [OPTION...] [USER@]HOST::SRC... [DEST]

      rsync [OPTION...] rsync://[USER@]HOST[:PORT]/SRC... [DEST]

Push: rsync [OPTION...] SRC... [USER@]HOST::DEST

     rsync [OPTION...] SRC... rsync://[USER@]HOST[:PORT]/DEST

```

  

Usages with just one SRC arg and no DEST arg will list the source files instead of copying.[^5][^3]

  

## DESCRIPTION

  

Rsync is a fast and extraordinarily versatile file copying tool that can copy locally, to/from another host over any remote shell, or to/from a remote rsync daemon. It offers a large number of options that control every aspect of its behavior and permit very flexible specification of the set of files to be copied.[^3][^5]

  

Rsync is famous for its **delta-transfer algorithm**, which reduces the amount of data sent over the network by sending only the differences between the source files and the existing files in the destination. This makes it widely used for backups and mirroring and as an improved copy command for everyday use.[^5][^3]

  

### Key Features

  

- Support for copying links, devices, owners, groups, and permissions[^5]

- Exclude and exclude-from options similar to GNU tar[^5]

- CVS exclude mode for ignoring the same files that CVS would ignore[^5]

- Can use any transparent remote shell, including ssh or rsh[^5]

- Does not require super-user privileges[^5]

- Pipelining of file transfers to minimize latency costs[^5]

- Support for anonymous or authenticated rsync daemons (ideal for mirroring)[^5]

  
  

## GENERAL OPERATION

  

Rsync copies files either to or from a remote host, or locally on the current host (it does not support copying files between two remote hosts). There are two different ways for rsync to contact a remote system:[^5]

  

1. **Using a remote-shell program** (such as ssh or rsh) - used when the source or destination path contains a single colon (:) separator after a host specification[^5]

2. **Contacting an rsync daemon directly via TCP** - happens when the source or destination path contains a double colon (::) separator after a host specification, or when an rsync:// URL is specified[^5]

  

## USAGE EXAMPLES

  

```bash

# Transfer all .c files to remote directory

rsync -t *.c foo:src/

  

# Recursive transfer with archive mode and compression

rsync -avz foo:src/bar /data/tmp

  

# Copy directory contents (note the trailing slash)

rsync -avz foo:src/bar/ /data/tmp

  

# Local copy with improved functionality

rsync -av /src/foo /dest

  

# List available modules from rsync daemon

rsync somehost.mydomain.com::

```

  
  

## SETUP

  

Rsync must be installed on both the source and destination machines. For remote transfers, modern rsync uses ssh for communications by default, but can be configured to use different remote shells like rsh or remsh. You can specify a remote shell using the `-e` command line option or by setting the `RSYNC_RSH` environment variable.[^2][^5]

  

The complete online manual with cross-linking is available at https://download.samba.org/pub/rsync/rsync.1.[^3][^5]

<span style="display:none">[^1][^10][^4][^6][^7][^8][^9]</span>

  

<div align="center">⁂</div>

  

[^1]: https://jhpce.jhu.edu/files/rsync/

  

[^2]: http://www.linuxguide.it/command_line/linux-manpage/do.php?file=rsync

  

[^3]: https://man.he.net/man1/rsync

  

[^4]: https://www.youtube.com/watch?v=OXcDbC9x9WE

  

[^5]: https://kaisenlinux.org/manpages/rsync.html

  

[^6]: https://man7.org/linux/man-pages/man1/rrsync.1.html

  

[^7]: https://www.unix.com/man_page/redhat/1/rsync/

  

[^8]: https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x10099.htm

  

[^9]: https://man.freebsd.org/cgi/man.cgi?query=rsync\&manpath=Darwin+8.0.1%2Fppc

  

[^10]: https://depts.washington.edu/sociolab/labmembers/documents/rsync-handout.pdf