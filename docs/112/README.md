ZET SCRIPT

Changing zet script to

```bash
#!/bin/sh
export KEG_CURRENT=~/Repos/github.com/rayct/zet/docs 
cd "$KEG_CURRENT" && exec keg "$@" cd - || exit 
```



---

Documentation By: **Raymond C. TURNER**

**Revision:** Saturday 4th November 2023