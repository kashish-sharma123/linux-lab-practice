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
