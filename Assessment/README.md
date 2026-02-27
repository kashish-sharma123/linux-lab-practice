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

**screenshot file*: `practical2`
