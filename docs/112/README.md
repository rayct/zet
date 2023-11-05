# ZET SCRIPT

* Changing zet script to

```bash
#!/bin/sh
export KEG_CURRENT=~/Repos/github.com/rayct/zet/docs 
cd "$KEG_CURRENT" && exec keg "$@" cd - || exit 
```

```bash
#!/bin/sh
export KEG_CURRENT="$HOME/Repos/github.com/rayct/zet/docs"
exec keg "$@"
```



---

Documentation By: **Raymond C. TURNER**

**Revision:** Sunday 5th November 2023