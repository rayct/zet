# Linux - Touch File Commands

To create a file in a directory using the `touch` command in a Unix-like operating system (e.g., Linux or macOS), you simply specify the path of the directory where you want to create the file followed by the desired filename. If the directory does not exist, you'll need to create it first using the `mkdir` command.

Here's the basic syntax:

```bash
touch /path/to/directory/filename
```

Replace `/path/to/directory` with the actual path to the directory where you want to create the file, and replace `filename` with the name you want to give to the new file.

For example, if you want to create a file named "example.txt" in a directory called "my_directory" located in your home directory, you can use the following command:

```bash
touch ~/my_directory/example.txt
```

This will create a new file named "example.txt" within the "my_directory" directory in your home directory.

If the directory does not exist, you can create it and the file in one step using the `-p` option with `mkdir`:

```bash
mkdir -p ~/my_directory && touch ~/my_directory/example.txt
```

The error message you're seeing, "rm: descend into write-protected directory '1076'," indicates that you are trying to remove a directory for which you do not have write permissions. To change the permissions on the directory and make it writable, you can use the `chmod` command.

Here's how you can use `chmod` to change the permissions of the directory:

```bash
chmod +w /path/to/directory
```

Replace `/path/to/directory` with the actual path to the "1076" directory. The `+w` option tells `chmod` to add write permissions to the directory.

For example, if the "1076" directory is located in your home directory, you can use:

```bash
chmod +w ~/docs/1076
```

Remove Read/Write Permissions

```bash
sudo rm -R 1076
```
---

**Main Command**
```bash
mkdir -p docs/1076 && touch docs/1076/README.md
```
---

After running this command, you should have write permissions on the "1076" directory, and you should be able to remove it using the `rm` command without encountering the "write-protected" error.

This command will create both the "my_directory" directory (if it doesn't exist) and the "example.txt" file within it.

---

</br>

Documentation By: **Raymond C. TURNER**

Last Updated: Wednesday 6th September 2023 @ 21:52 GMT