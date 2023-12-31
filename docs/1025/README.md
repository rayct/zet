# Linux Stuff - 2023

## New User with root
In Linux, the concept of a "full Administrator" is often referred to as the "root" user or "superuser." The root user has unrestricted access to the system, which can be risky if not managed properly. It's generally recommended to avoid using the root account for regular tasks and instead use a regular user account with the ability to run administrative commands using the `sudo` command.

However, if you still need to create a new user with administrative privileges, you can do so by adding the new user to the `sudo` group. Here's how:

1. **Create a New User:**

   Use the `adduser` command to create a new user. Replace `newuser` with the desired username.

   ```bash
   sudo adduser newuser
   ```

   Follow the prompts to set a password and additional user information.

2. **Add User to the sudo Group:**

   By default, most Linux distributions have a group named `sudo` that grants users the ability to execute administrative commands with elevated privileges. You need to add the new user to this group.

   ```bash
   sudo usermod -aG sudo newuser
   ```

   Replace `newuser` with the username you created.

3. **Test Administrative Privileges:**

   After adding the user to the `sudo` group, they should be able to run administrative commands using the `sudo` command. For example:

   ```bash
   sudo apt update
   sudo apt install some-package
   ```

   The user will be prompted to enter their own password to confirm their identity before running a command with elevated privileges.

It's important to note that providing full administrative privileges to a user carries security risks. It's generally better to grant administrative rights only as needed and to encourage users to use `sudo` for individual commands rather than always logging in as the root user. This helps maintain a more secure and manageable system.

---

## To move a directory and its contents to another directory in Linux, you can use the `mv` command. Here's the basic syntax:

```bash
mv source_directory destination_directory
```

Replace `source_directory` with the path of the directory you want to move, and `destination_directory` with the path of the target directory where you want to move the source directory.

Here's an example:

```bash
mv /path/to/source_directory /path/to/destination_directory
```

Make sure you have the necessary permissions to perform the move operation. If the target directory is on a different filesystem, the move operation might involve copying the files and then removing them from the source directory.

If you want to merge the contents of the source directory with an existing directory in the destination, you can use a trailing slash (`/`) at the end of the destination path:

```bash
mv /path/to/source_directory/* /path/to/destination_directory/
```

This will move the contents of `source_directory` into `destination_directory` without moving the `source_directory` itself.

Always be cautious when using the `mv` command, as moving or overwriting files and directories cannot be undone. Make sure to double-check your paths and intentions before proceeding.


Here's an example of how to check the existence of a file using the ls command:
`ls -l /usr/bin/lynx`

## Github Related
4. Export GPG_TTY environment variable: If the `--no-tty` flag doesn't work, try setting the `GPG_TTY` environment variable to point to your current TTY. This might help GPG locate the correct terminal and avoid the error.

   ```
   export GPG_TTY=$(tty)
   ```


---


# File Compression

To create a `.tar.gz` (also known as a tarball) archive in macOS, you can use the Terminal and the `tar` command. Here's how you can do it:

1. **Open Terminal**: You can find Terminal in the Utilities folder within the Applications folder, or you can search for it using Spotlight.

2. **Navigate to the directory**: Use the `cd` command to navigate to the directory containing the files and folders you want to archive. For example, if your files are located in the `Documents` folder, you can use:

   ```
   cd ~/Documents
   ```

3. **Create the tarball**: Use the `tar` command to create the `.tar.gz` archive. The basic syntax is:

   ```
   tar -czvf archive_name.tar.gz file1 file2 folder1 folder2
   ```

   - `-c`: Create a new archive
   - `-z`: Compress the archive using gzip
   - `-v`: Verbose mode (optional, shows the files being archived)
   - `-f`: Specify the archive filename

   For example, to create an archive named `my_archive.tar.gz` containing files `file1.txt` and `file2.txt`, you can use:

   ```
   tar -czvf my_archive.tar.gz file1.txt file2.txt
   ```

   To include an entire folder, such as `my_folder`, you can use:

   ```
   tar -czvf my_archive.tar.gz my_folder
   ```

4. **View the created archive**: You can list the contents of the created archive using the following command:

   ```
   tar -tzvf archive_name.tar.gz
   ```

   This will display a list of files and folders within the archive.

That's it! You've created a `.tar.gz` archive in macOS using the Terminal. Make sure to replace `archive_name` with the desired name for your archive and provide the appropriate file and folder names.

---

## Creating a .zip Archive:

To create a `.zip` archive in macOS, you can use the built-in `zip` command in the Terminal. Here's how:

1. **Open Terminal**: Just like before, locate and open the Terminal application.

2. **Navigate to the directory**: Use the `cd` command to navigate to the directory containing the files and folders you want to archive. For example:

   ```
   cd ~/Documents
   ```

3. **Create the .zip archive**: Use the `zip` command to create the `.zip` archive. The basic syntax is:

   ```
   zip -r archive_name.zip file1 file2 folder1 folder2
   ```

   - `-r`: Recursively include files and subdirectories
   - `archive_name.zip`: Specify the name of the archive

   For example, to create an archive named `my_archive.zip` containing files `file1.txt` and `file2.txt`, you can use:

   ```
   zip -r my_archive.zip file1.txt file2.txt
   ```

   To include an entire folder, such as `my_folder`, you can use:

   ```
   zip -r my_archive.zip my_folder
   ```

4. **View the created archive**: You can use the `unzip` command to list the contents of the created `.zip` archive:

   ```
   unzip -l archive_name.zip
   ```

## Other Compression Formats:

macOS supports various compression formats, including:

- `.tar.bz2`: Use the `tar` command with `-j` option to create a `.tar.bz2` archive (bzip2 compression).

  ```
  tar -cjvf archive_name.tar.bz2 file1 file2 folder1 folder2
  ```

- `.tar.xz`: Use the `tar` command with `-J` option to create a `.tar.xz` archive (xz compression).

  ```
  tar -cJvf archive_name.tar.xz file1 file2 folder1 folder2
  ```

Remember to replace `archive_name` with your desired archive name and specify the appropriate files and folders.


---

# gcc Development Tools

To install the GCC compiler and development tools on a Linux system, you typically use your system's package manager. The exact commands may vary depending on your Linux distribution. Here are instructions for a few popular Linux distributions:

**1. Ubuntu/Debian:**

Open a terminal and run the following commands:

```bash
sudo apt update
sudo apt install build-essential
```

The `build-essential` package includes GCC, the C library development files, and other essential build tools.

**2. CentOS/RHEL:**

Open a terminal and run the following commands:

```bash
sudo yum update
sudo yum group install "Development Tools"
```

This command installs a set of development tools, including GCC.

**3. Fedora:**

Open a terminal and run the following command:

```bash
sudo dnf install @development-tools
```

This command installs the development tools group, including GCC.

**4. Arch Linux:**

Open a terminal and run the following command:

```bash
sudo pacman -S base-devel
```

This command installs the base development tools, including GCC.

Once you have installed the development tools, including GCC, you can verify the installation by checking the GCC version:

```bash
gcc --version
```

This should display information about the installed GCC version and its related tools.

Please note that the package names and installation methods might vary slightly depending on your specific Linux distribution. If you're using a different distribution not mentioned above, you can search for the appropriate package names and installation commands in your distribution's documentation.

Keep in mind that the above instructions assume you have administrative privileges (sudo) on your system. If you are using a Linux distribution with a different package manager or have specific requirements, you may need to adjust the commands accordingly.


---


# venv

To create and manage a virtual environment (venv) in Linux, you can follow these steps:

1. Open a terminal.

2. Navigate to the directory where you want to create the virtual environment.

3. Run the following command to create a virtual environment named "myenv" (you can replace "myenv" with your desired environment name):

   ```
   python3 -m venv myenv
   ```

   Note: Make sure you have Python 3 installed on your system.

4. To activate the virtual environment, run:

   ```
   * source myenv/bin/activate
   * source mkdocs-material_venv/bin/activate
   ```

   Your terminal prompt should now change to indicate that you are in the virtual environment.

5. Install packages within the virtual environment using `pip`. For example:

   ```
   pip install package_name
   ```

6. To deactivate the virtual environment and return to the global Python environment, simply run:

   ```
   deactivate
   ```
7. Check your version of tkinter
   `python3 -m tkinter`

7. To delete the virtual environment, you can simply delete the directory associated with it. Be cautious when deleting directories, as this action is irreversible.

Remember to activate the virtual environment every time you want to work within it, and deactivate it when you're done.

Please note that the exact commands might vary slightly depending on your Linux distribution and setup. The above instructions assume you are using a standard Python installation on a Linux system.


---

# When dealing with directory names that have spaces in them, you need to take special care when using the command line. Spaces are used as delimiters in command-line arguments, so you need to properly escape or quote the directory names to ensure they are interpreted correctly. Here's how you can change directory names with spaces using various command-line interfaces:

1. **Linux and macOS (Bash shell):**

   Use quotes around the directory name or escape the spaces with a backslash:

   ```bash
   mv "old dir name with spaces" "new dir name"
   # or
   mv old\ dir\ name\ with\ spaces new\ dir\ name
   ```

2. **Windows (Command Prompt):**

   Enclose the directory names in double quotes:

   ```batch
   ren "old dir name with spaces" "new dir name"
   ```

   or

   ```batch
   rename "old dir name with spaces" "new dir name"
   ```

3. **Windows (PowerShell):**

   Enclose the directory names in single quotes or double quotes:

   ```powershell
   Rename-Item 'old dir name with spaces' 'new dir name'
   # or
   Rename-Item "old dir name with spaces" "new dir name"
   ```

4. **Windows Subsystem for Linux (WSL):**

   You can use the same commands as for Linux and macOS in the WSL terminal.

Remember to replace `"old dir name with spaces"` and `"new dir name"` with your actual directory names.

In general, using quotes around file or directory names with spaces is a safer approach, as it ensures that the entire name is treated as a single argument by the command-line interpreter. If you're working with scripting, be aware of the context in which you're using these commands, as different scripting languages may require slightly different approaches.

---

# Linux Distro Check

* `lsb_release -a`



---

# My Notes

`tar -czvf Random-Number-Generator-GUI-v0.1.1-beta.1.tar.gz Random-Number-Generator-GUI-v0.1.1-beta.1`


Choose the compression format based on your preferences and requirements. Each format has its own characteristics in terms of compression ratio and speed.

---

Documentation By: **Raymond C. TURNER**

**Last Updated:** Friday 6th October 2023