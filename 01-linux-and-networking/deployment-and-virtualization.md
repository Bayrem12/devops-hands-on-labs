# Deployment & Virtualization — Quick Reference

## 1. Web Servers

A web server receives HTTP requests and serves application content.

Common examples:

- Apache HTTP Server
- Nginx

### Apache

Common service names:

- Ubuntu: `apache2`
- CentOS / RHEL: `httpd`

```bash
sudo systemctl status apache2
sudo systemctl start apache2
```

On CentOS / RHEL, replace `apache2` with `httpd`.

Common Apache configuration locations:

| Distribution | Main Configuration |
|---|---|
| Ubuntu / Debian | `/etc/apache2/` |
| CentOS / RHEL | `/etc/httpd/conf/httpd.conf` |

Common document root: `/var/www/html`

## 2. Databases

A database stores and organizes application data.

Common relational databases:

- MySQL
- MariaDB
- PostgreSQL

Useful MySQL / MariaDB commands:

```sql
SHOW DATABASES;
CREATE DATABASE appdb;
USE appdb;
SHOW TABLES;
```

Common ports:

- MySQL / MariaDB: `3306`
- PostgreSQL: `5432`

## 3. Application Deployment

A basic deployment flow:

1. Prepare the server.
2. Install application dependencies.
3. Configure the application.
4. Configure the database if needed.
5. Start the application.
6. Configure network access.
7. Test the application.

Useful troubleshooting checks:

```bash
systemctl status SERVICE
journalctl -u SERVICE
ss -tuln
curl -I http://localhost
```

## 4. Virtualization

Virtualization allows multiple virtual machines (VMs) to run on one physical machine.

- **Host:** Physical machine running the virtualization software.
- **Guest:** Operating system running inside a VM.
- **Hypervisor:** Software that creates and manages VMs.

**VirtualBox** is an example of a hosted hypervisor.

## 5. Vagrant

Vagrant automates the creation and management of development environments.

```bash
vagrant init
vagrant up
vagrant status
vagrant ssh
vagrant halt
vagrant resume
vagrant reload
vagrant destroy
```

| Command | Purpose |
|---|---|
| `init` | Create a Vagrantfile |
| `up` | Create and start the VM |
| `status` | Check VM status |
| `ssh` | Connect to the VM |
| `halt` | Shut down the VM |
| `resume` | Resume a suspended VM |
| `reload` | Restart and apply configuration |
| `destroy` | Delete the VM |

The `Vagrantfile` defines the VM configuration, networking, shared folders, and provisioning.

## Remember

- A web server handles HTTP requests.
- A database stores application data.
- Virtualization provides isolated environments.
- Vagrant automates VM creation and configuration.
- Deployment requires correct application, service, database, and network configuration.

**Key takeaway:** A successful deployment depends on the application, its dependencies, the server environment, and network connectivity.