# 2023 Boost - Week 12

📺 <https://youtu.be/1Xjznp9thuw>

## Course Notes

lynx/w3m/chatGPT/cURL (Terminal web browsing for research)

1. Why search the Web from the terminal?

    * Note!

      **Don't Use Sysytem 76**

## Download files and create directory commands using `cURL`
1. lynx.cfg
    * Download the `lynx.cfg` using cURL:

    * `curl https://raw.githubusercontent.com/rwxrob/dot/main/lynx/lynx.cfg -O`
    * `-O` writes into to a file
      or
    * `-o lynx.cfg` Does the same.

1. lynx.lss
    * Download the `lynx.lss` using cURL:

    * `curl https://raw.githubusercontent.com/rwxrob/dot/main/lynx/lynx.lss -O`
    * `-O` writes into to a file
      or
    * `-o lynx.cfg` Does the same.

## Search using DuckDuck and Start the search by using the `?` command/character
1. Download the files as before
1. Write to a file and create the directory

    * `curl https://raw.githubusercontent.com/rwxrob/dot/main/scripts/duck > .local/bin/duck`

1. Give elevated privilages
    * `chmod +x ./local/bin/duck`
    * Check you have all the files `ls` or `tree -a .`
    * Then run `duck`
1. Install or fetch `urlencode`

    * `curl https://raw.githubusercontent.com/rwxrob/dot/main/scripts/urlencode > .local/bin/urlencode`
    *  `chmod +x ./local/bin/urlencode`

2. Parameter Expansion with BASH
    * List all Paths
    * `echo $PATH` 
    * `printf "${PATH//:/\\n}"`
    * `echo -e "${PATH//:/\\n}"`
    * Each one of the paths is where the system will look to run a program
    * Use this command to find every single file on your sytem and list file strucute tree.
    * `find .` and `tree .` or `tree -a .` to see everything.
    * Edit the `~/.bashrc` and add these commands known as `alias`
    * `set -o vi`
    * `alias path='echo -e "${PATH//:/\\n}"'`
3. Add the Alias `?`
    * Edit the `~/.bashrc` and add these commands known as `alias`
    * Then run the command `exec bash -l` everytime you make changes to the `.bashrc` to start a new login shell.
    * 
    * Note!!.. Here's an example of how to check the existence of a file using the ls command:
     
    * `ls -l /usr/bin/lynx`
  
    * Now run `path`
4. Making a file an Executable
    * `chmod +x <filename>`

5. which command (Known as The Locater Command)
    * eg: `which duck`
    * eg: `which lynx`

## w3m vs lynx
1. w3m - Text base Browser
    * **Note!!!.. Has a very very active user base.**



2. Isn't it slower to search from the terminal?



1. What if a page needs images or JavaScript to be understood?



1. What is the difference between `lynx` and `w3m`?



1. Can I get answers from ChatGPT from the command line?
   * Search through your terminal history.
   * `esc` then pres `k` then `\` then type `n` to scroll through the history or <type in the last terminal command you need>`
   * **Learn to SEARCH centricity**
1. Install chatGPT
   * `https://github.com/charmbracelet/mods` 
   * Fetch from `(rwxrob)` github.com repo.
   * `curl https://raw.githubusercontent.com/rwxrob/dot/main/scripts/gpt > .local/bin/gpt`
   * Now fetch the file
   * `curl -LO  https://github.com/charmbracelet/mods/releases/download/v0.2.0/mods_Linux_arm64.tar.gz -O`
   * Check File
   * `tar zxvf mods_Linux_arm64.tar.gz`
   * 
   * **TO PROTECT FROM TARBOMBS, MKDIR `MODS` DIRECTORY FIRST THEN `MV` INTO MODS DIR, THEN UNZIP**
   * 
   * First `mkdir mods`
   * Now move the file
   * `mv mods_Linux_arm64.tar.gz mods`
   * cd in `mods`
   * then unzip it into mods 
    `tar zxvf` <file_name>.tar.gz
   * move mods to ``./local/bin`
   * `mv mods/mods .local/bin/`
   * Now you can remove `mods` from your home directory'
   * `rm -rf mods`
   * `ls`
   * create the dir below.
   * `mkdir -p ~/.config/gpt`
   * Enter the your API key in the following file
   * `vi ~/.config/gpt`
   * echo something > `~/.config/gpt/token`
## Explaination of the above Unix shell command.
The command provided seems to be a Unix shell command that is likely used to write the text "something" to a file located at the path `~/.config/gpt/token`.

Let's break down the command step by step:

1. `echo something`: This part of the command is using the `echo` command, which is used to display text on the terminal. In this case, it is displaying the text "something".

2. `>`: This is called the "output redirection" operator. It is used to redirect the output of the command on the left (in this case, the output of `echo something`) into a file specified on the right.

3. `~/.config/gpt/token`: This is the path to the file where the output of the `echo` command will be written. It looks like an absolute file path, starting with `~` which is a shortcut for the user's home directory.

So, when you run the command `echo something > ~/.config/gpt/token`, it will create a file named `token` inside the `.config/gpt` directory in the user's home directory (for example, `/home/username/.config/gpt/token`), and the word "something" will be written into that file. If the file already exists, this command will overwrite its contents; if it doesn't exist, the command will create it.

This type of operation is commonly used to store configuration data or tokens in files for use by scripts, applications, or other processes. It's worth noting that the exact purpose of this command would depend on the context in which it's being used.


2. What else can I query from the command line using `curl`?

    * `curl https://raw.githubusercontent.com/rwxrob/dot/main/scripts/ix > .local/bin/ix`
    * 




Related:
<https://github.com/rwxrob/dot>

**Documentation By:** `Raymond C. TURNER`