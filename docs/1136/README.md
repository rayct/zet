# Linux Security Logs

In Linux, several logs can provide information about password changes or user authentication-related events. Here are some logs you can check:

1. **/var/log/auth.log or /var/log/secure:** This log typically records authentication-related information, including successful and failed login attempts, password changes, and authentication errors. Look for entries related to `passwd` or `su` commands.

2. **/var/log/wtmp:** This log maintains a record of all login and logout activity. It can help track when someone logged in or out of the system, but it might not specifically record password changes.

To check for changes specifically to the `su` password, it's crucial to review the logs around the time when the suspected password change occurred. Look for entries related to password modification commands or successful `su` attempts.

You can view these logs using commands like `cat`, `less`, or `grep` in the terminal. For instance:

```bash
sudo cat /var/log/auth.log | grep passwd
sudo cat /var/log/auth.log | grep su
sudo cat /var/log/secure | grep passwd
sudo cat /var/log/secure | grep su
sudo last -f /var/log/wtmp
```

*Remember, viewing logs typically requires elevated privileges (`sudo`), and interpreting the logs might require knowledge of the specific log formats and relevant timestamps. If you suspect unauthorized access or tampering with the system, it's essential to investigate thoroughly and consider taking security measures like changing passwords and enhancing system security configurations.*




---

Documentation By: **Raymond C. TURNER**

**Revision:** Monday 8th January 2024