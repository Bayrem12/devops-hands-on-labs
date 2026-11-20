# Linux Commands — Quick Reference

## 1. Filesystem

Linux uses a hierarchical filesystem starting from `/` (root).

| Directory | Purpose |
|---|---|
| `/` | Filesystem root |
| `/home` | User directories |
| `/root` | Root user's home |
| `/etc` | Configuration files |
| `/var` | Logs and variable data |
| `/tmp` | Temporary files |
| `/usr` | Applications and utilities |
| `/opt` | Optional software |
| `/var/www/html` | Common web-server document root |

## 2. Navigation & Files

```bash
pwd                 # Show current location
ls -lah             # List files with details
cd /etc             # Change directory
cd ..               # Go to parent directory
cd ~                # Go to home directory
touch file.txt      # Create empty file
mkdir -p a/b        # Create nested directories
cp file.txt backup.txt
mv old.txt new.txt
rm file.txt
```

## 3. Reading & Searching

```bash
cat file.txt
less file.txt
head -n 10 file.txt
tail -n 20 file.txt
tail -f /var/log/syslog
grep "error" app.log
find /var/log -name "*.log"
```

## 4. Disk & Memory

```bash
df -h               # Filesystem disk usage
du -sh directory    # Directory size
lsblk               # Block devices
free -h             # Memory usage
```

## 5. Package Management

Install and update software using the system's package manager.

| Distribution | Package Manager | Example |
|---|---|---|
| Ubuntu / Debian | APT | `sudo apt install nginx` |
| CentOS / RHEL | DNF | `sudo dnf install nginx` |

```bash
# Ubuntu / Debian
sudo apt update
sudo apt upgrade
sudo apt install nginx
sudo apt remove nginx

# CentOS / RHEL
sudo dnf check-update
sudo dnf upgrade
sudo dnf install nginx
sudo dnf remove nginx
```

## 6. Archives

```bash
tar -czf backup.tar.gz directory/
tar -xzf backup.tar.gz
```

- `-c`: Create archive
- `-x`: Extract archive
- `-z`: Use gzip compression
- `-f`: Specify archive filename

## Remember

- Linux commands are case-sensitive.
- Absolute paths start with `/`.
- Relative paths depend on your current directory.
- Use `man command` to read a command's manual.
- Use `command --help` for a quick reference.

**Key takeaway:** Learn how to navigate, inspect, manage, and troubleshoot the filesystem before automating Linux tasks.