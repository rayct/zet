# 2023 Boost - Week 12

📺 <https://youtu.be/1Xjznp9thuw>

## Course Notes

lynx/w3m/chatGPT/cURL (Terminal web browsing for research)

1. Why search the Web from the terminal?

    * Note!

      **Don't Use Sysytem 76**

## Download 2 files
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

    * Check you have all the files `ls`
  Parameter Expansion with BASH
    * List all Paths
    * `echo $PATH` 
    * `printf "${PATH//:/\\n}"`
    * `echo -e "${PATH//:/\\n}"`
    * Each one of the paths is where the system will look to run a program
    * Use this command to find every single file on your sytem.
    * `find .` and `tree .` or `tree -a .` to see everything.
    * Edit the `~/.bashrc` and add these commands
    * `set -o vi`
    * `alias path='echo -e "${PATH//:/\\n}"'`
    * Then run the command below
    * `exec bash -l`




1. Isn't it slower to search from the terminal?



1. What if a page needs images or JavaScript to be understood?



1. What is the difference between `lynx` and `w3m`?



1. Can I get answers from ChatGPT from the command line?



1. What else can I query from the command line using `curl`?




Related:
<https://github.com/rwxrob/dot>