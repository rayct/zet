# Understanding how to use octal notation with the `chmod`

Understanding how to use octal notation with the `chmod` command in Unix-like operating systems (such as Linux) is essential for setting file permissions efficiently and effectively. In the octal notation, permissions are represented using three digits: one for the owner, one for the group, and one for others.

Each digit represents a combination of read (4), write (2), and execute (1) permissions, and you add these numbers together to represent the desired permissions for each user group. Here's a breakdown:

- Read (r): 4
- Write (w): 2
- Execute (x): 1

Here are some common octal values for permissions:

- 7 (rwx): Read, write, and execute permission.
- 6 (rw-): Read and write permission.
- 5 (r-x): Read and execute permission.
- 4 (r--): Read-only permission.
- 3 (rwx): Write and execute permission.
- 2 (-w-): Write-only permission.
- 1 (--x): Execute-only permission.
- 0 (---): No permission.

To use octal notation with `chmod`, you assign permissions for the owner, group, and others using the octal value. For example:

```bash
chmod 755 file.txt
```

In this example:
- Owner gets read, write, and execute permissions (7).
- Group gets read and execute permissions (5).
- Others get read and execute permissions (5).

Here's another example to set read and write permissions for the owner, and read-only permission for others:

```bash
chmod 644 file.txt
```

In this example:
- Owner gets read and write permissions (6).
- Group gets read-only permission (4).
- Others get read-only permission (4).

Understanding octal notation and using it with `chmod` allows you to quickly and precisely set permissions on files and directories in a Unix-like environment.


---

Documentation By: **Raymond C. TURNER** (421ray)

**Last Updated:** Thursday 28th September 2023