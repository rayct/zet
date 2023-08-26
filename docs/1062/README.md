# Renaming multiple files in Linux using the command line can be done using various methods, such as `mv` (move) command, `rename` command, or even using shell scripting. Here are a few approaches:

### Renaming the boost 2023 files

`mv week1.md week01.md week2.md week02.md week3.md week03.md week4.md week04.md week5.md week05.md week6.md week06.md week7.md week07.md week8.md week08.md`

**Eg:** The command I've written seems to be correct for renaming those files if I want to add leading zeros to the numbers in the filenames. However, it could be a bit repetitive to write each filename explicitly. So You can use a loop or brace expansion to make it more concise.

Here's how you could do it using `brace expansion:`

```bash
for i in {1..8}; do
    mv "week$i.md" "week$(printf "%02d" $i).md"
done
```
---

In this loop, `{1..8}` generates the numbers from 1 to 8. The `printf "%02d" $i` part formats the number with leading zeros if needed, ensuring that it's two digits wide. So, week1.md becomes week01.md, week2.md becomes week02.md, and so on.

Remember to always test such operations on a smaller set of files or in a test environment before applying them to a large number of important files. This helps ensure you're getting the desired results without unintended consequences.

1. **Using `mv` Command:**
   The `mv` command can be used to rename files by moving them to the same directory with a new name.

   ```bash
   mv old_filename new_filename
   ```

   If you want to rename multiple files, you can use a loop or brace expansion:

   ```bash
   for file in old_prefix*; do
       mv "$file" new_prefix"${file#old_prefix}"
   done
   ```

   Here, replace `old_prefix` with the common prefix of the old filenames, and `new_prefix` with the desired new prefix.

2. **Using `rename` Command:**
   The `rename` command is used to rename multiple files using regular expressions. Note that this command might not be available by default on all systems. It's often installed as part of the `perl` package.

   ```bash
   rename 's/old_text/new_text/' files_to_rename*
   ```

   For example, to replace "old" with "new" in all files that start with "files_to_rename", you'd run:

   ```bash
   rename 's/old/new/' files_to_rename*
   ```

3. **Using Shell Scripting:**
   You can create a shell script to rename files based on various criteria using loops and string manipulation.

   ```bash
   #!/bin/bash

   for file in old_prefix*; do
       new_name="new_prefix${file#old_prefix}"
       mv "$file" "$new_name"
   done
   ```

   Make sure to give execute permissions to the script using `chmod +x script_name.sh`, and then run it using `./script_name.sh`.

*Remember to always create backups of your important files before performing bulk renaming operations to avoid accidental data loss.*

**Note!** Before proceeding, it's recommended to test these commands on a small set of files to ensure they work as expected for your specific use case.


---

Documentation by: **Raymond C. TURNER**

Last Updated: Saturday 26th August 2023 @ 18:25 GMT