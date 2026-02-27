# Lab 1 --Disk Monitoring Script

Created a Bash script disk_check.sh to monitor disk usage and generate an alert if usage exceeds a defined threshold. The script checks disk utilization using the df command and logs alerts to /tmp/disk_alert.log.

Steps performed:

Created script using vim

Set disk usage threshold

Extracted disk usage using df

Logged alerts with timestamp

Made script executable and executed it

Screenshots:

**Screenshot Filename:** `Task1.png`

**Screenshot Filename:** `Task1.1.png`

# Lab 2 – HTTP Traffic Capture

Captured HTTP network traffic using tcpdump and generated web requests using curl.

Steps performed:

Identified network interface using ip a

Captured HTTP packets with tcpdump

Generated traffic using curl

Observed TCP handshake and HTTP requests

Screenshots:

**Screenshot Filename:** `Task2.png`

**Screenshot Filename:** `Task2.1.png`

**Screenshot Filename:** `Task2terminal.png`

# Homework Tasks

1. Argument Counting Script

Created countargs.sh to print all command line arguments and count them.

Commands:

`vim countargs.sh`

`chmod +x countargs.sh`

`./countargs.sh apple banana mango`

Screenshot:

**Screenshot Filename:** `Homework1.png`
**Screenshot Filename:** `Homework1.2.png`

2. Process Using Maximum Memory

Identified the process using the highest memory.

Command:
`ps aux --sort=-%mem | head -2`

Screenshot:

**Screenshot Filename:** `Homework2.png`

3. Largest Directory in /var/log

Checked the largest directory in the log folder.

Command:
`sudo du -sh /var/log/* | sort -hr | head -1`

Screenshot:

**Screenshot Filename:** `Homework3.png`

4. Last 20 SSH Logs

Displayed recent SSH service logs.

Command:
`journalctl -u ssh -n 20`

Screenshot:

**Screenshot Filename:** `Homework4.png`

5. Disk Monitoring Automation

Automated the disk monitoring script using cron/systemd timer.

Commands:

`crontab -e`

`systemctl start disk_check.timer`

`systemctl status disk_check.timer`

Screenshot:

**Screenshot Filename:** `Homework5.png`
