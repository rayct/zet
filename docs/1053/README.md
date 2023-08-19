# BASH STUFF - 2023

## Opening Files with `xdg` in the current Directory

`xdg-*`
`xdg-open <FILENAME>`

---


After making changes to the `.bashrc` file, you typically don't need to restart the entire shell to apply the changes. Instead, you can source the `.bashrc` file in the current shell session to apply the changes immediately. Here's how you can do it:

1. **Edit `.bashrc` File:**
   Make the necessary changes to your `.bashrc` file using a text editor like `nano`, `vim`, or any other text editor of your choice. For example:
   
   ```bash
   nano ~/.bashrc
   ```

2. **Save and Close the Editor:**
   Save your changes and close the text editor.

3. **Source `.bashrc`:**
   To apply the changes without restarting the shell, use the `source` command or its shorthand `.` (dot):
   
   ```bash
   source ~/.bashrc
   # or
   . ~/.bashrc
   ```

   This command reloads the `.bashrc` file in the current shell session, applying any changes you made.

Keep in mind that some changes might require you to start a new shell session to take effect, especially if the changes involve environment variables or settings that affect the shell's behavior globally. In such cases, it's a good idea to start a new terminal window or session after editing the `.bashrc` file.

---

Documentation by: **Raymond C. TURNER**

Last Updated: 1 Day ago