# Linux and Github Stuff - 2

## This file is generated from information provided by the datasource.
Changes to it will not persist across an instance reboot.
To disable cloud-init's
network configuration capabilities, write a file
`/etc/cloud/cloud.cfg.d/99-disable-network-config.cfg` with the following:
`network: {config: disabled}`

!!! note "edit the netplan config file"

    /etc/netplan/50-cloud-init.yaml

    ```network:
    renderer: networkd
    ethernets:
        eth0:
        addresses:
            - 192.168.1.84/24
        nameservers:
            addresses: [1.1.1.1, 1.0.0.1]
        routes:
            - to: default
            via: 192.168.1.1
    version: 2
    ```

## Check if you are using https or SSH:
  `git remote -v`

To convert remote's URL from https to ssh. To check if remote's URL is ssh or https, use `git remote -v`.
To switch from https to ssh: `git remote set-url origin git@github.com:USERNAME/REPOSITORY.git`

## Switching remote URLs from SSH to HTTPS
Open Terminal.

Change the current working directory to your local project.

List your existing remotes in order to get the name of the remote you want to change.

$ git remote -v
> origin  git@github.com:OWNER/REPOSITORY.git (fetch)
> origin  git@github.com:OWNER/REPOSITORY.git (push)
Change your remote's URL from SSH to HTTPS with the git remote set-url command.

git remote set-url origin https://github.com/OWNER/REPOSITORY.git
Verify that the remote URL has changed.

$ git remote -v

## Verify new remote URL
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
The next time you git fetch, git pull, or git push to the remote repository, you'll be asked for your GitHub username and password. When Git prompts you for your password, enter your personal access token. Alternatively, you can use a credential helper like Git Credential Manager. Password-based authentication for Git has been removed in favor of more secure authentication methods. For more information, see "Managing your personal access tokens."

You can use a credential helper so Git will remember your GitHub username and personal access token every time it talks to GitHub.

## Switching remote URLs from HTTPS to SSH
Open Terminal.

Change the current working directory to your local project.

List your existing remotes in order to get the name of the remote you want to change.

`$ git remote -v`
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
Change your remote's URL from HTTPS to SSH with the git remote set-url command.

`git remote set-url origin git@github.com:OWNER/REPOSITORY.git`
Verify that the remote URL has changed.

$ git remote -v

## Verify new remote URL

> origin  git@github.com: OWNER/REPOSITORY.git (fetch)
> origin  git@github.com: OWNER/REPOSITORY.git (push)
Troubleshooting: No such remote '[name]'
This error means that the remote you tried to change doesn't exist:

$ git remote set-url sofake https://github.com/octocat/Spoon-Knife
> fatal: No such remote 'sofake'
Check that you've correctly typed the remote name.

Renaming a remote repository
Use the git remote rename command to rename an existing remote.

The git remote rename command takes two arguments:

An existing remote name, for example, origin
A new name for the remote, for example, destination
Example of renaming a remote repository
These examples assume you're cloning using HTTPS, which is recommended.

$ git remote -v

# Change remote name from 'origin' to 'destination'

$ git remote -v

## Verify remote's new name
> destination  https://github.com/OWNER/REPOSITORY.git (fetch)
> destination  https://github.com/OWNER/REPOSITORY.git (push)
Troubleshooting: Could not rename config section 'remote.[old name]' to 'remote.[new name]'
This error means that the old remote name you typed doesn't exist.

You can check which remotes currently exist with the git remote -v command:

$ git remote -v

## View existing remotes

> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
Troubleshooting: Remote [new name] already exists
This error means that the remote name you want to use already exists. To solve this, either use a different remote name, or rename the original remote.

Removing a remote repository
Use the git remote rm command to remove a remote URL from your repository.

The git remote rm command takes one argument:

A remote name, for example, destination
Removing the remote URL from your repository only unlinks the local and remote repositories. It does not delete the remote repository.

Example of removing a remote repository
These examples assume you're cloning using HTTPS, which is recommended.

$ git remote -v

## View current remotes

> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
> destination  https://github.com/FORKER/REPOSITORY.git (fetch)
> destination  https://github.com/FORKER/REPOSITORY.git (push)

$ git remote rm destination

# Remove remote

$ git remote -v
## Verify it's gone
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
Note: git remote rm does not delete the remote repository from the server. It simply removes the remote and its references from your local repository.

Troubleshooting: Could not remove config section 'remote.[name]'
This error means that the remote you tried to delete doesn't exist:

$ git remote rm sofake
> error: Could not remove config section 'remote.sofake'
 - Check that you've correctly typed the remote name.

---

# Linux Server Notes - July 2023

## Downloading Content from the Internet via the Command Line.

To download files via the command line in Ubuntu Server, you can use various tools such as `wget`, `curl`, or `scp`. Here are the basic steps to download files using these tools:

1. **Using wget:**
   - Open a terminal or SSH into your Ubuntu Server.
   - Run the following command to download a file using wget:
     ```
     wget <URL>
     ```
     Replace `<URL>` with the actual URL of the file you want to download.
   - The file will be downloaded to the current directory.

2. **Using curl:**
   - Open a terminal or SSH into your Ubuntu Server.
   - Run the following command to download a file using curl:
     ```
     curl -O <URL>
     ```
     Replace `<URL>` with the actual URL of the file you want to download.
   - The file will be downloaded to the current directory.

3. **Using scp:**
   - Open a terminal or SSH into your Ubuntu Server.
   - Run the following command to download a file from a remote server using scp:
     ```
     scp user@remote_host:/path/to/remote/file /path/to/local/directory
     ```

     Example: 
     
     ```
     scp ray@jayde:/home/ray/downloads/Rocky-9.2-x86_64-dvd.iso /Users/ray/downloads
     ```

     Replace `user` with your username, `remote_host` with the IP address or hostname of the remote server, `/path/to/remote/file` with the path to the file on the remote server, and `/path/to/local/directory` with the path to the directory where you want to save the file on your local server.
   - You will be prompted to enter your password for the remote server, and then the file will be downloaded to the specified local directory.

Choose the appropriate method based on your requirements and the availability of the tools on your Ubuntu Server.

---

# To create a "downloads" folder with write permissions on Ubuntu Server, you can follow these steps:

1. Open a terminal or SSH into your Ubuntu Server.

2. Navigate to the desired parent directory where you want to create the "downloads" folder. For example, if you want to create it in the user's home directory, you can use the following command:
   ```
   cd ~
   ```

3. Create the "downloads" folder using the `mkdir` command:
   ```
   mkdir downloads
   ```

4. Set the appropriate write permissions on the "downloads" folder. You can use the `chmod` command to modify the permissions. For example, to give read, write, and execute permissions to the owner and read and write permissions to the group and others, you can use the following command:
   ```
   chmod 755 downloads
   ```

   Note: Adjust the permissions based on your specific requirements. The "755" permission set grants read, write, and execute permissions to the owner and read and execute permissions to the group and others.

5. Verify the permissions by running the `ls -l` command. You should see the permissions listed along with the "downloads" folder:
   ```
   ls -l
   ```

   The output should show the permissions for the "downloads" folder, similar to the following example:
   ```
   drwxr-xr-x  2 user group 4096 Jul  7 09:00 downloads
   ```

   The permissions "drwxr-xr-x" indicate that it is a directory ("d"), the owner has read, write, and execute permissions ("rwx"), the group and others have read and execute permissions ("r-x"), and the "2" represents the number of items in the folder.

You have now created a "downloads" folder with appropriate write permissions on your Ubuntu Server. You can use this folder to download files and perform read and write operations as needed.

| Number      | Permission Type         |  Symbol   |
| :---------- | :---------------------- | :-------- |
| `0`         | No Permission           | -         |
| `1`         | Execute                 | -x        |
| `2`         | Write                   | -w-       |
| `3`         | Execute + Write         | -wx       |
| `4`         | Read                    | r-        |
| `5`         | Read + Execute          | r-x       |
| `6`         | Read + Write            | rw-       |
| `7`         | Read + Write + Execute  | rwx       |


# Changing File Permissions
The `chmod` command is used to alter the permissions of a file. It may be used to add or remove permissions symbolically. For example, to add execute permissions for the owner of a file you would run:


`$ chmod u+x file_name`

Or, to add read and write permissions for the group that owns the file, you would run:


`$ chmod g+rw file_name`

Instead of adding permissions, the symbolic syntax of chmod can also be used to subtract or set to some absolute value as shown in these examples:

`$ chmod o-w file_name`
`$ chmod u=rwx,g=rx,o= file_name`

The `chmod` command can also explicitly set permissions using a numerical representation. For example, to set permissions on a file to `rwxrwxr–,` you would run:

`$ chmod 774 file_name`


# Bash Command Examples
1. Start an interactive shell session:
`bash`

1. Start an interactive shell session without loading startup configs:
`# bash --norc`

1. Execute specific [c]ommands:
`bash -c "echo 'bash is executed`

1. Execute a specific script:
`bash /path/to/script.sh`

1. Execute a specific script while printing each command before executing it:
`bash -x /path/to/script.sh`

1. Execute a specific script and stop at the first [e]rror:
`bash -e /path/to/script.sh`

1. Execute specific commands from stdin:
`echo "echo 'bash is executed'" | bash`



# Create a new user on Ubuntu Server

To create a new user in Ubuntu Server, you can follow these steps:

1. Log in to your Ubuntu Server as a user with administrative privileges or switch to the root user.

2. Open a terminal or connect to the server via SSH.

3. Use the `adduser` command to create a new user. Replace `<username>` with the desired username for the new user.

```
sudo adduser <username>
```

4. You will be prompted to set a password for the new user. Enter a strong password and confirm it.

5. The `adduser` command will prompt you to enter additional information about the new user. You can either provide the information or leave it blank by pressing Enter to skip.

6. Once the user is created, you can grant administrative privileges to the user by adding them to the `sudo` group. This will allow the user to run commands with `sudo` and perform administrative tasks.

```
sudo usermod -aG sudo <username>
```

7. The new user is now created and can log in to the server using SSH or a terminal.

Remember to replace `<username>` with the actual username you want to create. You can choose any username that complies with the system's username requirements.

# Switch to new user

To switch to a new user in Ubuntu Server, you can use the `su` command followed by the username. Here are the steps to switch to a new user:

1. Open a terminal or connect to the server via SSH.

2. Run the following command to switch to the new user. Replace `<username>` with the actual username you want to switch to:

```
su <username>
```

3. If you're switching to a user other than root, you'll be prompted to enter the password for that user. Enter the password and press Enter.

4. Once the correct password is entered, you will be logged in as the new user.

After switching to the new user, you will have access to that user's permissions and privileges. If you need to perform administrative tasks, you can use the `sudo` command before the desired command to execute it with root privileges.

Please note that switching to another user requires administrative privileges. If you are not currently logged in as a user with administrative privileges, you may need to prefix the `su` command with `sudo` and enter the password for the current user with administrative privileges.



# Podman Notes
## Run Alpine

  `sudo podman run -it --rm alpine`

---

Documentation By: **Raymond C. TURNER**

Last Updated: Saturday 27th August 2023 @ 18:33 BST