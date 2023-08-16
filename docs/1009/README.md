# .SSH 

## Removing old offending ssh key's from `known_hosts`

    `@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@`
    `@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @`
    `@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@`

    IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
    Someone could be eavesdropping on you right now (man-in-the-middle attack)!
    It is also possible that a host key has just been changed.
    The fingerprint for the ED25519 key sent by the remote host is
    SHA256:6V+ewOaO6dRUMMYm5MbnKiVZQ2yLCadjnUgmB8PSYXo.
    Please contact your system administrator.
    Add correct host key in /home/ray/.ssh/known_hosts to get rid of this message.
    Offending ECDSA key in /home/ray/.ssh/known_hosts:5
    remove with:
    ssh-keygen -f "/home/ray/.ssh/known_hosts" -R "192.168.1.84"
    Host key for 192.168.1.84 has changed and you have requested strict checking.
    Host key verification failed.

    Type the Following Command
        1. 'ssh-keygen -f "/home/ray/.ssh/known_hosts" -R "192.168.1.84"`

**Documentation By:** `Raymond C. TURNER`