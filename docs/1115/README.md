# Linux Commands | October 2023

To extract files from an archive on a Linux system, you can use various command-line tools depending on the type of archive. Here are some commonly used commands:

1. **For .zip files**:
   ```
   unzip file.zip
   ```

2. **For .tar.gz or .tgz files** (commonly used for compressed tar archives):
   ```
   tar -xzvf file.tar.gz
   ```

3. **For .tar.bz2 files** (compressed tar archives with bzip2 compression):
   ```
   tar -xjvf file.tar.bz2
   ```

4. **For .tar files** (uncompressed tar archives):
   ```
   tar -xvf file.tar
   ```

5. **For .gz files** (gzip compression):
   ```
   gunzip file.gz
   ```

6. **For .bz2 files** (bzip2 compression):
   ```
   bunzip2 file.bz2
   ```

7. **For .xz files** (xz compression):
   ```
   unxz file.xz
   ```

8. **For .7z files** (7-Zip archives):
   ```
   7z x file.7z
   ```

Remember to replace `file` with the actual name of the archive file you want to extract. Additionally, you can specify the destination directory using the `-C` option for `tar` or the `-d` option for `unzip`. For example:

```bash
tar -xzvf file.tar.gz -C /path/to/destination
unzip file.zip -d /path/to/destination
```

This will extract the contents of the archive to the specified destination directory.

---

## cp command
The `cp` command in Linux is used to copy files or directories from one location to another. The basic syntax of the `cp` command is as follows:

```
cp [options] source destination
```

Here's how you can use the `cp` command:

1. **Copying a File:**
   To copy a file from one location to another, you would use the `cp` command like this:

   ```
   cp source_file destination_directory
   ```

   For example, to copy a file named `file.txt` to a directory called `backup`, you would use:

   ```
   cp file.txt backup/
   ```

2. **Copying a Directory:**
   To copy an entire directory and its contents, you can use the `-r` or `-R` (recursive) option. For example:

   ```
   cp -r source_directory destination_directory
   ```

   For instance, to copy a directory named `folder` and all its contents to a directory named `backup`, you would use:

   ```
   cp -r folder backup/
   ```

3. **Preserving File Attributes:**
   You can use the `-p` option to preserve file attributes such as timestamps and ownership while copying:

   ```
   cp -p source_file destination_directory
   ```

4. **Interactive Mode:**
   If you want to be prompted for confirmation before overwriting files, you can use the `-i` option:

   ```
   cp -i source_file destination_directory
   ```

5. **Force Overwriting:**
   To forcefully overwrite the destination file if it already exists, you can use the `-f` option:

   ```
   cp -f source_file destination_directory
   ```

Remember to replace `source_file` and `destination_directory` with the actual file or directory paths you want to copy from and to. The options provided give you control over the copying process.

---

## touch command

To create an empty file in a specific directory on a Linux system, you can use the `touch` command. Here's how you can do it:

```bash
touch /path/to/directory/filename
```

Replace `/path/to/directory` with the actual path to the directory where you want to create the file, and replace `filename` with the name you want to give to the new empty file.

For example, if you want to create an empty file named "example.txt" in a directory called "documents," you would run the following command:

```bash
touch /path/to/documents/example.txt
```

```bash
touch 1119/README.md
```

This will create the "example.txt" file in the "documents" directory.

---

Documentation By: **Raymond C. TURNER**

**Last Updated:** Wednesday 18th October 2023