#  Differences between wget and curl

1. What is cURL and what can it do?
1. How cURL compares to wget
1. How to download a file from a website with cURL
1. How to follow redirects
1. How to download and untar a file automatically
1. How to authenticate with cURL
1. How to download headers with cURL
1. How to use quiet mode with cURL


wget	curl
Wget is a simple tool designed to perform quick downloads	Curl on the other hand is a much more powerful tool. It can achieve a lot more as compared to Wget.
Wget is command line only	Curl is powered by libcurl
Wget supports only HTTP, HTTPS, and FTP protocols	Curl supports a lot more protocols, these are DICT, FILE, FTP, FTPS, Gopher, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS, Telnet and TFTP
Wget offers the ability to download recursively	It’s difficult to achieve recursive access to a web resource with curl
wget is more focused on Linux-based distros	Curl is available on multiple platforms with many web utilities leveraging curl to interact with the web




### Download a file from a website with cURL
`curl https://example.com/linux.iso --output linux.iso`

**Documentation By:** `Ray C. TURNER`