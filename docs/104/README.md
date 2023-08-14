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