## Go programming language Installion on a Raspberry Pi using the following steps:

Step 1: Update and upgrade the system

Before installing any new software, it's a good idea to ensure that your Raspberry Pi is up-to-date. Open a terminal window and run the following commands:

```bash
sudo apt update
sudo apt upgrade
```

Step 2: Download the Go binary

Visit the official Go website (https://golang.org/dl/) and find the latest stable version of Go for ARM architecture. Look for the "Linux ARMv6l" architecture, which is the architecture used in most Raspberry Pi models.

For example, at the time of my last update, you might download Go version 1.17.1 for ARMv6l with the following command:

You can fetch Using `wget` or `cURL` as listed below

 ```bash
wget https://go.dev/dl/go1.20.6.linux-arm64.tar.gz
```
 ```bash
curl -O https://go.dev/dl/go1.20.6.linux-arm64.tar.gz
```

Step 3: Install Go

Now that you have the Go binary tarball, you can extract it and install Go:

```bash
sudo tar -C /usr/local -xzf go1.17.1.linux-armv6l.tar.gz
```

Step 4: Set Go environment variables

You need to set the `PATH` and `GOPATH` environment variables so that Go commands are available in your terminal.

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

Step 5: Refresh the environment variables

To apply the changes without having to log out and log back in, run the following command in the terminal:

```bash
source ~/.profile
```

Step 6: Verify the installation

To check if Go is installed correctly, run:

```bash
go version
```

You should see the installed Go version printed in the terminal.

That's it! You've successfully installed Go on your Raspberry Pi.

Please note that the version numbers and download URLs may have changed since my last update, so make sure to check the official Go website for the most recent version available for ARM architecture.