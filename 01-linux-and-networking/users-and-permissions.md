# Users & Permissions — Quick Reference

## 1. Users and Groups

Linux uses users and groups to control access to system resources.

```bash
whoami                  # Current user
id                      # User and group IDs
who                     # Logged-in users
sudo adduser john       # Create a user (Ubuntu)
sudo useradd john       # Create a user (RHEL/CentOS)
sudo passwd john        # Set or change password
sudo groupadd developers
sudo usermod -aG developers john
```

## 2. File Ownership

Every file has an owner and a group.

```bash
ls -l
sudo chown john file.txt
sudo chown john:developers file.txt
sudo chgrp developers file.txt
```

## 3. File Permissions

Three permission types:

| Permission | Meaning | Numeric Value |
|---|---|---|
| Read (`r`) | View contents | 4 |
| Write (`w`) | Modify contents | 2 |
| Execute (`x`) | Execute a file / access a directory | 1 |

Permissions apply to:

- `u`: Owner
- `g`: Group
- `o`: Others

Example:

```text
-rwxr-xr--
```

| Owner | Group | Others |
|---|---|---|
| rwx | r-x | r-- |
| 7 | 5 | 4 |

## 4. chmod

Change file permissions.

```bash
chmod 755 script.sh
chmod 644 file.txt
chmod +x script.sh
```

- `755`: Owner can read/write/execute; others can read/execute.
- `644`: Owner can read/write; others can read.

## 5. sudo

Run a command with elevated privileges.

```bash
sudo command
sudo -l
```

Use `sudo` only when necessary.

## Remember

- `chown` changes ownership.
- `chgrp` changes group ownership.
- `chmod` changes permissions.
- `sudo` runs commands with elevated privileges.
- Avoid giving everyone unnecessary write or execute permissions.

**Key takeaway:** Linux permissions control who can access and modify files and directories.