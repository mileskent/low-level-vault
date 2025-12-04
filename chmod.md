See [here](https://linuxize.com/post/chmod-command-in-linux/) for more info

The syntax of the `chmod` command when using the symbolic mode has the following format:

```sh
chmod [OPTIONS] [ugoa…][-+=]perms…[,…] FILE...
```

The first set of flags (`[ugoa…]`), users flags, defines which users classes the permissions to the file are changed.

- `u` - The file owner.
- `g` - The users who are members of the group.
- `o` - All other users.
- `a` - All users, identical to `ugo`.

If the users flag is omitted, the default one is `a` and the permissions that are set by [umask](https://linuxize.com/post/umask-command-in-linux/) are not affected.

The second set of flags (`[-+=]`), the operation flags, defines whether the permissions are to be removed, added, or set:

- `-` Removes the specified permissions.
- `+` Adds specified permissions.
- `=` Changes the current permissions to the specified permissions. If no permissions are specified after the `=` symbol, all permissions from the specified user class are removed.

The permissions (`perms...`) can be explicitly set using either zero or one or more of the following letters: `r`, `w`, `x`, `X`, `s`, and `t`. Use a single letter from the set `u`, `g`, and `o` when copying permissions from one to another users class.

When setting permissions for more than one user classes (`[,…]`), use commas (without spaces) to separate the symbolic modes.

# Examples
Give the members of the group permission to read the file, but not to write and execute it:
```
  chmod g=r filename
```

Remove the execute permission for all users:
```
chmod a-x filename
```

Recursively remove the write permission for other users:
```
chmod -R o-w dirname
```

Remove the read, write, and execute permission for all users except the file’s owner:
```
chmod og-rwx filename
```

The same thing can be also accomplished by using the following form:
```
chmod og= filename
```

Give read, write and execute permission to the file’s owner, read permissions to the file’s group and no permissions to all other users:
```
chmod u=rwx,g=r,o= filename
```

Add the file’s owner permissions to the permissions that the members of the file’s group have:
```
chmod g+u filename
```

Add a sticky bit to a given directory:
```
chmod o+t dirname
```