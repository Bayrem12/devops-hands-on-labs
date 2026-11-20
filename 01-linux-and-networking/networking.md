# Networking — Quick Reference

## 1. IP Addresses

An IP address identifies a device on a network.

- **IPv4:** Example `192.168.1.10`
- **Loopback:** `127.0.0.1` refers to the local machine.
- **localhost:** A hostname commonly mapped to `127.0.0.1`.

```bash
ip addr show          # Show network interfaces and IPs
ip route              # Show routing table
hostname -I           # Show assigned IP addresses
```

## 2. Ports

A port identifies a service or application endpoint on a machine.

| Port | Common Service |
|---|---|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL / MariaDB |
| 5432 | PostgreSQL |

```bash
ss -tuln              # Show listening TCP/UDP ports
```

## 3. TCP vs UDP

| TCP | UDP |
|---|---|
| Connection-oriented | Connectionless |
| Reliable delivery | No delivery guarantee |
| Maintains packet order | No guaranteed packet order |
| Example: HTTPS, SSH | Example: DNS queries, streaming |

## 4. DNS

DNS translates domain names into IP addresses.

Example:

```text
example.com → 93.184.216.34
```

Useful commands:

```bash
nslookup example.com
dig example.com
getent hosts example.com
```

Important files:

- `/etc/hosts` — Local hostname-to-IP mappings.
- `/etc/resolv.conf` — DNS resolver configuration (may be managed by the system).

## 5. Connectivity Troubleshooting

```bash
ping 8.8.8.8
ping example.com
curl -I https://example.com
ip route
ss -tuln
```

- `ping`: Tests network reachability.
- `curl`: Makes HTTP requests and inspects responses.
- `ip route`: Shows routing information.
- `ss`: Inspects sockets and listening ports.

## 6. SSH

SSH provides secure remote access to another machine.

```bash
ssh user@server_ip
ssh -p 2222 user@127.0.0.1
```

Common SSH files:

- `~/.ssh/` — User SSH configuration and keys.
- `~/.ssh/authorized_keys` — Public keys allowed to access an account.
- `/etc/ssh/sshd_config` — SSH server configuration.

## 7. Firewalls

A firewall controls incoming and outgoing network traffic.

Common tools:

- `firewalld` — Firewall management commonly used on RHEL/CentOS.
- `ufw` — Simplified firewall management commonly used on Ubuntu.

```bash
# firewalld
sudo firewall-cmd --state
sudo firewall-cmd --list-all

# UFW
sudo ufw status
```

Only allow the network access a service actually needs.

## 8. Virtual Machine Networking

| Mode | Main Purpose |
|---|---|
| NAT | VM accesses external networks through the host |
| Bridged | VM appears as a device on the physical network |
| Host-only | Communication between host and VM, and often other host-only VMs |
| NAT Network | VMs can communicate with each other and access external networks through NAT |

**Remember:** IP addresses identify machines, ports identify services, and DNS resolves names into addresses.

**Key takeaway:** When a connection fails, check the IP, route, DNS resolution, listening port, and firewall.