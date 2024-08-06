### File Permission Types

- **Read (r)**: Allows reading the contents of the file or listing the contents of a directory.
- **Write (w)**: Allows modifying the contents of the file or making changes to the directory contents (e.g., creating, deleting files).
- **Execute (x)**: Allows executing the file (if it's a script or binary) or entering the directory (changing into the directory).

### Permission Categories

- **Owner (u)**: The user who owns the file.
- **Group (g)**: The group that owns the file.
- **Others (o)**: All other users.

### Viewing File Permissions

Use the `ls -l` command to list files with their permissions:
```bash
ls -l
```

Example output:
```
-rwxr-xr--
```

- The first character indicates the type (`-` for file, `d` for directory, `l` for link).
- The next nine characters are the permissions for the owner, group, and others, in groups of three (rwxr-xr--):
    - `rwx` (owner): read, write, execute
    - `r-x` (group): read, execute
    - `r--` (others): read

### Changing File Permissions

Use the `chmod` command to change file permissions:
```bash
chmod [permissions] [file]
```

Permissions can be set using symbolic (letters) or numeric (octal) representation.

Symbolic Representation:
```bash
chmod u+rwx,g+rx,o+r file.txt
```

- `u`: owner
- `g`: group
- `o`: others
- `+`: add permission
- `-`: remove permission
- `=`: set exact permission

Numeric Representation:
```bash
chmod 755 file.txt
```

Each permission is represented by a number:
- `r = 4`
- `w = 2`
- `x = 1`

Sum the numbers for each category:
- Owner: `rwx = 4 + 2 + 1 = 7`
- Group: `r-x = 4 + 0 + 1 = 5`
- Others: `r-- = 4 + 0 + 0 = 4`

### Changing Ownership

Use the `chown` command to change file owner and group:
```bash
chown [owner]:[group] file.txt
```

To change only the owner:
```bash
chown [owner] file.txt
```

To change only the group:
```bash
chown :group file.txt
```

### Special Permissions

Special permissions are available for files and directories and provide additional privileges over the standard permission sets that have been covered.

#### Setuid (SUID)
- **Description**: Setuid is the special permission for the user access level and always executes as the user who owns the file, no matter who is passing the command.
- **Usage**: Often used for executables that require higher privileges to perform specific tasks. For example, the `passwd` command has setuid permissions so that it can change the password file as the root user.
- **Setting SUID**:
```sh
chmod u+s filename
```
- **Example**:
```sh
chmod 4755 script.sh
```
This command sets the setuid permission on `script.sh` with the resulting permissions `-rwsr-xr-x`.

#### Setgid (SGID)
- **Description**: SGID allows a file to be executed as the group owner of the file. For directories, a file created in the directory has its group ownership set to the directory owner. This is helpful for directories used collaboratively among different members of a group because all members can access and execute new files.
- **Usage**: Useful for shared directories where files should inherit the group of the directory.
- **Setting SGID**:
```sh
chmod g+s filename
```
- **Example**:
```sh
chmod 2755 directory/
```
This command sets the setgid permission on `directory/` with the resulting permissions `drwxr-sr-x`.

#### Sticky Bit
- **Description**: The "sticky bit" is a directory-level special permission that restricts file deletion, meaning only the file owner can remove a file within the directory.
- **Usage**: Commonly used on shared directories like `/tmp` to prevent users from deleting each other's files.
- **Setting Sticky Bit**:
```sh
chmod +t directory/
```
- **Example**:
```sh
chmod 1777 /tmp
```
This command sets the sticky bit on `/tmp` with the resulting permissions `drwxrwxrwt`.

### Summary

#### Setuid
- **Command**: `chmod u+s filename`
- **Numeric Representation**: `4XXX`
- **Example**: `chmod 4755 script.sh`

#### Setgid
- **Command**: `chmod g+s filename`
- **Numeric Representation**: `2XXX`
- **Example**: `chmod 2755 directory/`

#### Sticky Bit
- **Command**: `chmod +t directory/`
- **Numeric Representation**: `1XXX`
- **Example**: `chmod 1777 /tmp`