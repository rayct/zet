# Lynx - CMD Line Internet

#!/bin/sh
#exec w3m "duckduckgo.com/lite?kd=-1&kp=-1&q=$*"
url="https://lite.duckduckgo.com/lite?kd=-1&kp=-1&q=$(urlencode "$*")" # 🦆
#chat "🦆 searching: $* $url"
exec lynx "$url"
#exec w3m "$url"
#exec lynx "duckduckgo.com/lite?q=$*" # 🦆
#exec lynx "duckduckgo.com/lite?q=$*"

---

Documentation By: **Raymond C. TURNER**

**Revision:** Wednesday 29th November 2023