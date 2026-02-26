#  Day 3 – Linux Networking & Web Server Lab
This lab focuses on:

* Network configuration & identity

* Internet connectivity & DNS

* Web server setup (Nginx)

* Firewall rules & local domain testing


#  Task 1 – Verify Network Identity
Commands & Purpose:

* ip addr       - Shows network interfaces, IPs, and interface status

* ip route      - Displays routing table & default gateway

* hostname -I   - Displays system IP address cleanly

* ping -c 4 172.31.0.1  - Tests gateway connectivity

 **Screenshot Filename:** `Task1.png`

#  Task 2 – Internet Connectivity

Ping by IP:
* ping  8.8.8.8  - Tests raw internet connectivity

Ping by Domain:
* ping google.com   - Checks DNS resolution & connectivity

Trace Route:
* traceroute google.com  - Displays packet path

**Screenshot Filename:** `Task2.png,Task2.1.png,Task2.2.png,Task2.3.png`

#  Task 3 – DNS Analysis

 * dig google.com         -Resolves IP, DNS server, TTL
   
 * cat /etc/resolv.conf   - Checks system DNS resolver
   
 * nslookup google.com    - Alternative DNS check

 **Screenshot Filename:** `Task3.png`

 #  Task 4 – Nginx Web Server Setup

 * sudo apt install nginx -y                     - Install server
  
 * echo "Hello " | sudo tee /var/www/html/index.html
 
 * curl http://localhost                         - Test locally
 
 * sudo systemctl status nginx                   - Verify service

 **Screenshot Filename:** `Task4.png`

 #  Task 5 – Open Ports
* ss -tuln  -Lists listening ports (HTTP:80, HTTPS:443, DNS:53)

 **Screenshot Filename:** `Task5.png`

 #  Task 6 – Application Connectivity
 
 * curl -I http://localhost  # Fetch only HTTP headers
   
 * wget http://localhost     # Download homepage content

**Screenshot Filename:** `Task6.png,Task6.1.png`

#  Task 7 – Firewall (UFW)

* sudo ufw enable
* sudo ufw allow 80
* sudo ufw allow 443
* sudo ufw deny 22       - SSH blocked; tested via port 443 due to WiFi restriction
* sudo ufw status

**Screenshot Filename:** `Task7.png`

#  Task 8 – Local Domain (/etc/hosts)

* sudo vim /etc/hosts

# Add:

* 127.0.0.1 mytest.local

* curl http://mytest.local  # Test local domain

**Screenshot Filename:** `Task8.png,Task8.1.png,Task8.2.png`






