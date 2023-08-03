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
    * Note!!..Here's an example of how to check the existence of a file using the ls command:
    * `ls -l /usr/bin/lynx`
    * Now run `path`
4. Making a file an Executable
    * `chmod +x <filename>`



## which command (The Locater Command)

    * eg: `which duck`
    * eg: `which lynx`





1. Isn't it slower to search from the terminal?



1. What if a page needs images or JavaScript to be understood?



1. What is the difference between `lynx` and `w3m`?



1. Can I get answers from ChatGPT from the command line?



1. What else can I query from the command line using `curl`?




Related:
<https://github.com/rwxrob/dot>

**Documentation By:** `Raymond C. TURNER`