 

# on ubuntu server 24 how do i now which directories are network directories?

  

On Ubuntu Server 24, you can identify network directories (network-mounted filesystems) using several different commands that will help you distinguish them from local storage

## Primary Methods to Identify Network Directories

### Using the `mount` Command

The most straightforward way is to filter the mount command output for network filesystem types:
```bash

mount -t cifs,nfs,nfs4

```

This shows only CIFS (SMB/Windows shares) and NFS mounts. You can also use grep to filter:
  ```bash

mount | grep -E "(cifs|nfs|nfs4)"

```
  
### Using the `df` Command

The `df -h` command displays mounted filesystems with their usage statistics, and network mounts will show their network paths:
```bash

df -h

```
  

Network directories will appear with paths like `//192.168.0.32/share` for CIFS or `192.168.4.100:/home/user/dir` for NFS.
  

### Using the `findmnt` Command

  
The `findmnt` command provides detailed information about mounted filesystems in a tree format:
```bash

findmnt -t cifs,nfs,nfs4

```

  

This specifically shows only network filesystems. For a list format instead of tree view:
```bash

findmnt -l -t cifs,nfs,nfs4

```

## Understanding Network Filesystem Types

  

### Common Network Filesystem Types

- **cifs**: Windows/SMB shares mounted using the CIFS protocol[^5][^1]

- **nfs**: NFS version 3 mounts[^4]

- **nfs4**: NFS version 4 mounts (displayed as separate filesystem type)[^4]

### Checking `/proc/mounts` Directly

You can examine the kernel's view of mounted filesystems:
```bash

cat /proc/mounts | grep -E "(cifs|nfs|nfs4)"

```
  
The third column in `/proc/mounts` shows the filesystem type, making it easy to identify network mounts.
## Additional Identification Methods

### Using `lsblk` Command

While `lsblk` primarily shows block devices, it can help identify what's **not** a network mount:
```bash

lsblk -f

```

Network mounts won't appear in `lsblk` output since they're not local block devices.[^8][^3]
### Detailed Mount Information

For comprehensive mount information including options:
```bash

findmnt -D

```

This shows mount propagation and other details that can help identify network mounts.[^2]

## Practical Examples

Network mounts typically appear with these characteristics:

- **CIFS/SMB**: `//server-ip/share-name` format

- **NFS**: `server-ip:/path/to/export` format

- **Filesystem types**: `cifs`, `nfs`, or `nfs4` in the type column

The network directories will be mounted at local mount points (like `/mnt/networkshare` or `/media/share`) but the source will clearly indicate the network location.
<span style="display:none">[^10][^11][^12][^13][^14][^15][^16][^17][^18][^19][^20][^21][^22][^23][^24][^25][^26][^27][^28][^29][^30][^31][^32][^33][^34][^35][^36][^37][^38][^39][^40][^41][^42][^43][^9]</span>
