# Creating a Samba share on Linux Mint involves configuring the Samba server and defining the shared folders. Here are step-by-step instructions to create a simple Samba share:

### 1. Install Samba:

```bash
sudo apt update
sudo apt install samba
```

### 2. Create a Shared Folder:

You need to choose a folder on your system that you want to share. For example, let's create a folder named "shared_folder" in the home directory:

```bash
mkdir ~/shared_folder
```

### 3. Configure Samba:

Edit the Samba configuration file `/etc/samba/smb.conf`. You can use a text editor such as `nano` or `gedit`:

```bash
sudo nano /etc/samba/smb.conf
```

Add the following lines at the end of the file:

```plaintext
[shared_folder]
   comment = Shared Folder
   path = /home/your_username/shared_folder
   browseable = yes
   read only = no
   guest ok = yes
   create mask = 0777
   directory mask = 0777
```

Replace "your_username" with your actual username.

### 4. Set Samba Password:

Set a Samba password for the user you want to use to access the share. This should be a valid system user:

```bash
sudo smbpasswd -a your_username
```

### 5. Restart Samba:

After making changes to the configuration, restart the Samba service:

```bash
sudo systemctl restart smbd
```

### 6. Firewall Configuration:

If you are using a firewall, allow Samba traffic:

```bash
sudo ufw allow Samba
```

### 7. Access the Share:

You should now be able to access the Samba share from another machine using the path `\\your_mint_machine_ip\shared_folder` (replace "your_mint_machine_ip" with the actual IP address of your Linux Mint machine).

If you encounter any issues, review the Samba logs for error messages:

```bash
sudo tail -f /var/log/samba/log.smbd
```

Adjust the configuration and permissions as needed.

Keep in mind that this is a basic setup, and you may want to refine the configuration based on your specific requirements for security, access control, and additional features.



---

Documentation By: **Raymond C. TURNER**

**Revision:** Wednesday 23rd January 2024