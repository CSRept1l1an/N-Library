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

