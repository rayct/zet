# Install Go - Linux

To install Go (Golang) on Linux from the official Go website, follow these steps:

1. **Download the Go binary**:
   
   Visit the official Go download page at [https://golang.org/dl/](https://golang.org/dl/) using your web browser. Choose the appropriate version for your operating system. For this example, we'll use Linux.

2. **Select the version**:
   
   Select the version of Go you want to install. You'll typically want the latest stable release. Click on the link to download the binary distribution for Linux.

3. **Download the Go tarball**:

   The download page will provide a link to a `.tar.gz` file. Click on the link to download the tarball containing the Go distribution.

4. **Open a terminal**:

   Open a terminal on your Linux system.

5. **Move the downloaded file to the desired location**:
   
   Use the `mv` command to move the downloaded tarball to the desired location. For example, if you want to install Go in `/usr/local`, you can use the following command:
   
   ```bash
   mv ~/Downloads/go<VERSION>.linux-amd64.tar.gz /usr/local
   ```

   Replace `<VERSION>` with the actual version number you downloaded.

6. **Extract the tarball**:
   
   Use the `tar` command to extract the tarball:
   
   ```bash
   cd /usr/local
   sudo tar -xvf go<VERSION>.linux-amd64.tar.gz
   ```

   Replace `<VERSION>` with the actual version number you downloaded.

7. **Set the PATH environment variable**:
   
   To use Go, you need to add the Go binary directory to your `PATH` environment variable. Edit your shell's profile configuration file (e.g., `~/.bashrc`, `~/.bash_profile`, or `~/.zshrc`) to include the following line:

   ```bash
   export PATH=$PATH:/usr/local/go/bin
   ```

   Save the file and then run:

   ```bash
   source ~/.bashrc   # or ~/.bash_profile, or ~/.zshrc
   ```

   This will apply the changes to your current shell session.

8. **Verify the installation**:
   
   Verify that Go is installed correctly by running:

   ```bash
   go version
   ```

   You should see the version of Go you installed.

---

Documentation By: **Raymond C. TURNER**

Last Update: Wednesday 20th September 2023