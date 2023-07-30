## Go programming language Installion on a Raspberry Pi using the following steps:

Go Version: 
* `Sunday July 30th 2023`

* `go1.20.6.linux-arm64.tar.gz`

Step 1: Update and upgrade the system (same as before)

```bash
sudo apt update
sudo apt upgrade
```

Step 2: Use `curl` to download the Go binary

Visit the official Go website (https://golang.org/dl/) and find the latest stable version of Go for ARM architecture. Look for the "Linux ARMv6l" architecture, which is the architecture used in most Raspberry Pi models.

For example, at the time of my last update, you might download `Go` version 1.20.6 for ARMv6l with the following `curl` command:

```bash
curl -L -O https://golang.org/dl/go1.20.6.linux-arm64.tar.gz
```

Step 3: Verify the downloaded file

After downloading the file, verify if it is not corrupted by running the `file` command:

```bash
file go1.20.6.linux-arm64.tar.gz
```

You should see something like this if the file is valid:

```
go1.20.6.linux-armv6l.tar.gz: gzip compressed data, from Unix, original size modulo 2^32 691861248
```

Step 4: Install Go

Now, proceed with the installation by extracting the tarball:

```bash
sudo tar -C /usr/local -xzf go1.20.6.linux-arm64.tar.gz
```

Step 5: Set Go environment variables (same as before)

Edit your `~/.profile` or `~/.bashrc` file using a text editor like `nano`:

```bash
nano ~/.profile
```

Add the following lines to the end of the file:

```bash
export PATH=$PATH:/usr/local/go/bin
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

Save and exit the text editor (press `CTRL + X`, then `Y`, and finally `ENTER`).

Step 6: Refresh the environment variables (same as before)

To apply the changes without having to log out and log back in, run the following command in the terminal:

```bash
source ~/.profile
```

Step 7: Verify Go environment variables

To check if the Go environment variables have been set correctly run:

```bash
go env
```

Step 8: Verify the installation (same as before)

To check if Go is installed correctly, run:

```bash
go version
```

You should see the installed Go version printed in the terminal.

If you encounter any issues, please double-check the downloaded file's integrity and make sure you have the correct download URL for the ARMv6l architecture.

**Documentation By:** `Raymond C. TURNER`