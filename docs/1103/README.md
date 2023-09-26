# Bash Shell

## Reset or clear the commands in your Bash shell history:

1. **Clear the Current Session History:**
   
   You can clear the current session's command history using the `history` command with the `-c` option:
   
   ```bash
   history -c
   ```

   This will clear the history for the current session, but it won't affect the overall Bash history file.

2. **Clear the Entire Bash History:**

   If you want to clear your entire Bash history, you can delete the history file. By default, the history is usually stored in `~/.bash_history`:
   
   ```bash
   rm ~/.bash_history
   ```

   After running this command, the history will be cleared, and the file will be recreated the next time you close the terminal.

3. **Remove Individual Commands from History:**

   If you want to remove specific commands from your history, you can use the `history` command to view your history and then use the `-d` option to delete a specific entry. For example:
   
   ```bash
   history # View the history and note down the command number you want to remove
   history -d <command_number> # Delete the desired command by specifying its number
   ```

   Replace `<command_number>` with the actual number of the command you want to delete.

Remember that clearing or deleting your command history is a permanent action, and the history won't be recoverable after deletion. Also, keep in mind that if you're on a shared system or have security concerns, it's essential to be cautious about clearing your history, especially if it contains sensitive information.



---

Documentation By: **Raymond C. TURNER**

**Last Updated:** Tuesday 12th September 2023