
# 📘 Essential Linux Networking Commands for DevOps

> This guide covers critical networking commands used in system administration, DevOps, and cloud infrastructure troubleshooting.

---

## 🔗  `ip`
Replaces the older `ifconfig` tool. Used for IP address and interface management.
The ip command is used to display and modify networking parameters on Linux systems. It can handle IP addresses ,Routing tables,Network interfaces.

### 📌 Syntax:
```bash
ip [OPTIONS] OBJECT COMMAND
```

### ✅ Common Examples:
```bash
ip addr show
ip a     # shorthand
ip route # Show routing table
```

---

## 🌐 `ping`
Checks network connectivity with another host.
ping is a network utility used to test the reachability of a host on an IP network and to measure round-trip time (RTT) for messages sent from the source to a destination.

It uses ICMP (Internet Control Message Protocol) echo requests and waits for echo replies.

### 📌 Syntax:
```bash
ping [OPTIONS] destination
```
- DESTINATION: IP address or hostname (e.g., 8.8.8.8, google.com)


### ✅ Examples:
```bash
ping google.com
ping -c 4 192.168.1.1 # Send only 4 packets
ping -W 5 4 192.168.1.1 # Timeout in 5 secs if destination not reply
ping -i 2 google.com # Ping with interval of 2 seconds  
ping -i 2 -c 4 -W 5 google.com # Ping with multiple options
```

### 🧠 Notes
ping runs indefinitely by default (until stopped with Ctrl+C)

### 🚀 Common ping Command Options

| Option           | Description                           |
| ---------------- | ------------------------------------- |
| `-c COUNT`       | Send a fixed number of packets        |
| `-i INTERVAL`    | Interval between packets (in seconds) |
| `-W TIMEOUT`     | Timeout for a reply (in seconds)      |
| `-q`             | Quiet output (summary only)           |
| `-s PACKET_SIZE` | Specify packet size (in bytes)        |
| `-t TTL`         | Set Time-To-Live for packets          |
| `-4`             | Use IPv4 only                         |
| `-6`             | Use IPv6 only                         |


---

## 🔐 `telnet`
Used to connect to remote machines over TCP.
The telnet command is used to interact with remote hosts using the TELNET protocol.
Network administrators and developers can use Telnet to test services and verify if ports are open.

### 📌 Syntax:
```bash
telnet [hostname/IP] [port]
```

### ✅ Example:
```bash
telnet localhost 80
telnet 14.45.89.90 22 # Test SSHD Port Connectivity
telnet 192.168.1.10 3306 # Test MySQL port connectivity
```

---

## 📡 `netstat` (Deprecated, use `ss`)
**netstat** (network statistics) is a legacy CLI tool used to monitor network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.

📌 Note: netstat is part of the net-tools package and is now largely replaced by tools like ss, ip.Still, it's widely used in legacy systems and scripts.

### 📌 Syntax:
```bash
netstat [OPTIONS]
```

### ✅ Example:
```bash
sudo netstat -tualnp
netstat -antp
```

---

## 🔁 `ss`
Replaces `netstat`, faster and more informative.
**ss** (Socket Statistics) is a fast and efficient utility used to display detailed information about network sockets. It can show much of the same information as netstat but is faster and more flexible.

It comes pre-installed with most modern Linux distributions and is part of the iproute2 package.

### 📌 Syntax:
```bash
ss [OPTIONS]
```

### ✅ Example:
```bash
sudo ss -tulanp
ss -tuln
ss -s
```

---

## 📶 `traceroute`
Tracks the route packets take to a destination.
traceroute is a network diagnostic tool used to track the path that packets take from your machine to a remote host. It displays each hop along the route and the time taken to reach each one.
It helps identify network bottlenecks, latency, or unreachable routers.

### If traceroute is not installed:

```
sudo apt install traceroute   # Debian/Ubuntu
sudo yum install traceroute   # RHEL/CentOS
```


 Syntax:
```bash
traceroute [destination]
```

### ✅ Example:
```bash
traceroute google.com
```

---

## 📥  `curl`
**curl** (Client URL) is a command-line tool used to transfer data to or from a server using supported protocols like HTTP, HTTPS, FTP, SFTP, SCP, and more.

It is widely used in DevOps, automation, scripting, and API testing.

### 📌 Syntax:
```bash
curl [OPTIONS] URL
```

### ✅ Examples:
```bash
curl https://example.com # Get Call
curl -v telnet://12.35.89.40:22 # This attempts to initiate a connection to a service running on port 22 on Given Host/IP
curl -I https://google.com # Fetch HTTP headers only
curl -O https://example.com/file.zip # Download a file and save with original name
curl -o file.html https://site.com  # Download a file and save with custom name
curl -X POST -d "username=admin&password=secret" https://example.com/login # Send a POST request with data
curl -X POST -H "Content-Type: application/json" -d '{"name":"balaji"}' https://api.example.com/user # Send JSON data in a POST request
curl -v https://example.com # Verbose.It will Displays: Request and response headers ,HTTP status codes,SSL negotiation,Connection details
```

---

## 📤 `wget`
Downloads files via HTTP, HTTPS, or FTP.
wget is a non-interactive command-line utility used for downloading files from the web. It supports HTTP, HTTPS, and FTP protocols and is ideal for automated downloads, mirroring websites, and retrieving data in scripts.

### 📌 Syntax:
```bash
wget [OPTIONS] URL
```

### 📥 Installation
wget is usually pre-installed. If not:

```
sudo apt install wget     # Debian/Ubuntu
sudo yum install wget     # RHEL/CentOS

```
### ✅ Example:
```bash
wget https://example.com/file.zip  # Download file with original name.

wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.105/bin/apache-tomcat-9.0.105.tar.gz #Download file with original name.

wget -O tomcat.tar.gz https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.105/bin/apache-tomcat-9.0.105.tar.gz # #Download and save with a different name.

```


---

## 🧠 `nslookup`
nslookup (Name Server Lookup) is a command-line tool used for querying DNS (Domain Name System) to obtain domain name or IP address mapping, or for any other specific DNS record.

### 📌 Syntax:
```bash
nslookup [domain]
```

### ✅ Example:
```bash
nslookup google.com  # Get IP Address of a Domain
nslookup example.com 8.8.8.8 # Use Specific DNS Server
```

⚠️ Notes

nslookup is considered deprecated in favor of dig and host for scripting.
Still very useful for quick manual DNS lookups.

---

## 🧠  `dig`
**dig** is a powerful and flexible command-line tool for querying DNS name servers. It provides detailed answers that are useful for troubleshooting DNS issues and inspecting DNS records.

### 📌 Syntax:
```bash
dig [options] [domain] [query-type] [@dns-server]
```

### Installation (if not installed)

- sudo yum install bind-utils
```
sudo yum install bind-utils # Redhat/AmazonLinux/CentOs

sudo apt update  # Debian/Ubuntu
sudo apt install dnsutils # Debian/Ubuntu

```

### ✅ Example:
```bash
dig google.com  # Basic A Record Lookup
dig +short google.com # Get Just the IP Address (Short Output)
dig @8.8.8.8 facebook.com  # Use Specific DNS Server 8.8.8.8 is a Google DNS Server
dig google.com +trace # trace DNS Resolution Path
```

⚠️ Notes

nslookup is considered deprecated in favor of dig and host for scripting.
Still very useful for quick manual DNS lookups.


---

## 🔗  `hostname` and `hostnamectl`

**hostname** command is used to display or set the system's hostname. Unlike hostnamectl, it's older and doesn't provide as many features but is still widely used.


### 📌 Syntax:
```bash
hostname [OPTION] [new_name]
```

### ✅ Example:
```bash
hostname # Show Current Hostname
sudo hostname webserverone #  Temporarily Until Reboot.This only updates the current session. To make it permanent, also update /etc/hostname.
hostname -f # Show FQDN (Fully Qualified Domain Name)
```


**hostnamectl** is a command-line tool to query and change the system hostname and related settings on systems running systemd.It allows setting:
Static hostname (permanent)
Transient hostname (temporary)


### 📌 Syntax:
```bash
hostnamectl [OPTIONS] [COMMAND]
hostnamectl set-hostname <new-name>
```

### ✅ Example:
```bash
hostnamectl # Show Current Hostname and Info
hostnamectl set-hostname webserverone #  Set Static Hostname (Persists After Reboot).This sets the hostname stored in /etc/hostname.
sudo hostnamectl set-hostname devops-temp --transient # Set Transient Hostname (Lost on Reboot):
```