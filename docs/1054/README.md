# VIM STUFF - 2023

## To delete all content from a file using the Vim text editor, you can use the following steps:

1. Open the file in Vim:
   ```
   vim filename
   ```

2. Once the file is open in Vim, press `Esc` to ensure you're in Normal mode.

3. Use the following command to delete all lines in the file:
   ```
   :%d
   ```

   Explanation:
   - `:` puts you in command mode.
   - `%` refers to all lines in the file.
   - `d` is the delete command.

4. After entering the command, press `Enter`.

This will delete all the content from the file. If you want to save the changes, you can use the `:w` command to write the changes to the file, followed by `:q` to quit Vim. If you want to save and quit in one step, you can use `:wq`.

Remember that using `:w` or `:wq` commands will save the file even if it's now empty. If you don't want to save the empty file, you can use `:q!` to forcefully quit Vim without saving.

## In Vim, you can copy (yank) and paste content using a combination of commands. Here's how you can do it:

1. **Copying (Yanking) Text:**
   To copy (yank) text in Vim, follow these steps:

   a. Move your cursor to the beginning of the text you want to copy.
   
   b. Press `v` to enter Visual mode. This allows you to select text.
   
   c. Move the cursor to select the desired text. The selected text will be highlighted.
   
   d. Once you've selected the text, press `y` to yank (copy) the selected text.

2. **Pasting Text:**
   To paste the copied text in Vim:

   a. Move the cursor to the position where you want to paste the text.

   b. Press `p` to paste the copied text after the cursor position.
   
   If you want to paste the copied text before the cursor position, press `P` (uppercase "P") instead.

Remember, you can yank and paste entire lines using the same approach. Instead of selecting characters, just position your cursor on the line you want to yank, and use `yy` to yank the line and `p` to paste it.

Additionally, if you want to yank and paste without entering Visual mode, you can use the following commands:

- To yank the entire line: `yy`
- To paste after the cursor: `p`
- To paste before the cursor: `P`

These commands can be quite versatile for copying and pasting text within Vim.


## In Vim, the undo command allows you to revert changes you've made to the text. The basic command to undo is:

```
u
```

Here's how it works:

1. While in Normal mode, press `u`. This will undo the most recent change you made.

2. If you want to undo multiple changes, press `u` multiple times to continue undoing changes step by step in reverse chronological order.

3. To redo changes that you've undone, you can press `Ctrl` + `r`.

Remember that Vim's undo functionality is linear, so each undo operation undoes the most recent change. If you want more advanced undo capabilities, you can consider using Vim's undo tree feature or external plugins.

## What TODO if you Created a Vi file and are unable to exit due to a no write permission

Here's what todo
`esc +:w /tmp/somebakup.txt`

---

Documentation By: **Raymond C. TURNER**

Last Updated: Wednesday 23rd August 2023 @ 18:22 BST