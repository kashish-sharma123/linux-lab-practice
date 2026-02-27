# Permission & umask

`umask` (User Mask) controls the default permissions removed when a new file or directory is created.

Default permissions:

File → 666 (rw-rw-rw-)

Directory → 777 (rwxrwxrwx)

Example:

If `umask` is 022

For files:

`666 - 022 = 644`

Permission becomes:

`rw-r--r--`

For directories:

`777 - 022 = 755`

Permission becomes:

`rwxr-xr-x`

Thus, `umask` restricts permissions by removing certain access rights.

**screenshot file* `practical1.md`

The `umask` command controls the default permission settings for newly created files and directories.
A umask value of 022 ensures that only the owner can modify files, while group and others can only read them, thereby improving system security.

# Create user `intern1` with `/bin/bash` and expire in 7 days

In Linux, the `useradd` command is used to create a new user account. The `-s` option sets the default login shell.

1. Create the user with bash shell

`sudo useradd -s /bin/bash intern1`

Explanation:

`sudo` – run with admin privileges

`useradd` – create a new user

`-s /bin/bash` – sets /bin/bash as the default shell

`intern1` – username

2. Set account expiry in 7 days

`sudo chage -E $(date -d "+7 days" +%Y-%m-%d) intern1`

Explanation:

`chage` – modify user account expiry settings

`-E` – sets the account expiration date

`+7 days` – account will expire after 7 days

Check expiry:

`chage -l intern1`

**screenshot file*: `practical2.md`

# Generate SSH Key Pair and Enable Passwordless Login

1. Generate SSH Key Pair

Use the `ssh-keygen` command to create a public and private key.

2. Add Public Key to `authorized_keys`

`cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys`

This allows the system to accept the key for login.

3. Set Proper Permissions

`chmod 700 ~/.ssh`

`chmod 600 ~/.ssh/authorized_keys`

4. Test Passwordless Login

`ssh -i ~/.ssh/id_rsa localhost`
 **sccrenshot file*`practical3.md`

 **screenshot file*`practical3.1.md`

 # Package management

 1. Install `htop`

`sudo apt update`

`sudo apt install htop`

`apt update` updates package lists

`apt install htop` installs the htop monitoring tool

2. Find which package provides `/bin/bash`

`dpkg -S /bin/bash`

Output:

`bash: /bin/bash`

**screenshot file*`practical4.md`

# Create a Cron Job to Run /usr/bin/date Every Minute

A cron job is used in Linux to schedule tasks that run automatically at specific time intervals.

1. Edit Crontab

Open the crontab file for the current user:

`crontab -e`

2. Add the Cron Job

Add the following line:

`* * * * * /usr/bin/date >> /tmp/cron_test.log`

Explanation:

* `* * * * *` - runs the command every minute

* `/usr/bin/date` - prints the current date and time

* `>>` - appends the output

* `/tmp/cron_test.log` - log file where output is stored

3. Show the Cron Jobs

To display the scheduled cron jobs:

`crontab -l`

**screenshot file*`practical5.md`

# Systemd Service and Timer

1. Create a service file

Create `/etc/systemd/system/hello.service`

[Unit]
Description=Hello Systemd Service

[Service]

Type=oneshot

ExecStart=/bin/bash -c 'echo "hello from systemd" >> /tmp/hello.txt'

This service runs once and writes “hello from systemd” to /tmp/hello.txt.

2. Create a timer file

Create `/etc/systemd/system/hello.timer`

[Unit]
Description=Run hello service every 2 minutes

[Timer]

OnBootSec=1min

OnUnitActiveSec=2min

Unit=hello.service

[Install]

WantedBy=timers.target

This timer triggers the service every 2 minutes.

3. Reload systemd

This reloads systemd so it recognizes the new service and timer.

4. Enable and start the timer

This enables the timer and starts it immediately.

5. Check active timers

`systemctl list-timers`

**screenshot file*`practical6.md,practical6.1.md,practical6.2.md`

