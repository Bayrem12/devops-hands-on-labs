# Processes & Services — Quick Reference

## 1. Processes

A process is a running instance of a program.

```bash
ps aux                  # List running processes
ps -ef                  # Detailed process list
top                     # Live process monitoring
pgrep nginx             # Find process by name
```

## 2. Process Management

```bash
command &
jobs
fg
kill PID
kill -9 PID
```

- `&`: Run a command in the background.
- `jobs`: Show background jobs in the current shell.
- `fg`: Bring a job to the foreground.
- `kill PID`: Send the default termination signal.
- `kill -9 PID`: Force termination (use only when necessary).

## 3. Services and systemd

A service is a background program managed by the operating system.

`systemd` is a common Linux service manager.

```bash
systemctl status nginx
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl enable nginx
sudo systemctl disable nginx
```

| Command | Purpose |
|---|---|
| `start` | Start a service now |
| `stop` | Stop a service |
| `restart` | Restart a service |
| `status` | Check its state |
| `enable` | Start automatically at boot |
| `disable` | Prevent automatic startup |

## 4. Logs

Logs help identify errors and understand system activity.

```bash
journalctl
journalctl -u nginx
journalctl -u nginx -f
journalctl -b
```

Common log locations:

- `/var/log/` — System and application logs.
- `journalctl` — Logs collected by systemd.

## Remember

- A process is a running program.
- A service is a background application, often managed by systemd.
- `systemctl` manages services.
- `journalctl` helps investigate service and system issues.

**Key takeaway:** When an application is not working, check its process, service status, and logs.