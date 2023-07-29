# TMUX
# 2023 Boost - Week 11

📺 <https://youtu.be/Tgct-GlBUM4>

1. What is a "multiplexer" and why should I care?
1. How do I install, configure and use screen?
1. Why should I use tmux? What's the difference between screen and tmux?
1. How do I install, configure, and use tmux?
1. How can I extend tmux?
1. Why not use Vim panes instead?

Related:

* <https://tmuxguide.readthedocs.io/en/latest/tmux/tmux.html>


# Screens
### Key Combinations
1. List any active Screens

    `screen -ls`

1. Default Command - qeued up ready accept another command then press

    `ctl + a` then `w`

1. Get to the cmd line

    `ctl + a +:`

2. Create a new Screen or Screens

    `ctl+a` then press `c`

3. Switching Screens

    `ctl+A+A` 

1. To switch between screens

    Hold down `ctl` double press `A`

1. Detaching a Screen

    `screen -d`

1. Reattach a Screen

    `screen -r`

# TMUX - Using a Custom `.conf`
### Note! The meta Key in TMUX is `ctl+b` as apposed to Screens `ctl+a`
1. Create a new Screen

    `ctl+b` then press `c`

1. Switch Screens

    `ctl+b` then press corresponding No: Eg: Screen 1 =`0`Screen 2 = `1` Screen 3 = `2` and so on.

1. Windows preview list all windows in tree form

    `ctl+b` then press `w`

1. Split panes - Vertically

    `ctl+a` then press `h` and `l` to go back and forth.

1. Copy and Paste between panes
   * `ctl+a` then press `[` to copy
   * then switch panes as described above
   * then `ctl+a` then `]` to paste in to next pane


**Documentation By:** `Raymond C. TURNER`