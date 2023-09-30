# Honeypot using Python

A basic example of a honeypot using Python and the `socket` library. 

Note!..Keep in mind that setting up and using honeypots requires careful consideration of security and legal implications. Honeypots can potentially attract malicious activity, so it's essential to use them responsibly and within legal boundaries.

In this example, I'll create a simple TCP honeypot that listens on a specific port and logs incoming connections. The purpose of this honeypot is to collect information about potential attackers.

```python
import socket
import datetime

def honeypot(port):
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(('0.0.0.0', port))
    server_socket.listen(5)
    print(f"[*] Listening on 0.0.0.0:{port}")

    while True:
        client_socket, addr = server_socket.accept()
        print(f"[*] Connection from: {addr[0]}:{addr[1]} at {datetime.datetime.now()}")

        # Log the connection details to a file
        with open('honeypot_log.txt', 'a') as log_file:
            log_file.write(f"Connection from: {addr[0]}:{addr[1]} at {datetime.datetime.now()}\n")
        
        client_socket.close()

if __name__ == '__main__':
    port = 12345  # Change this to the desired port number
    honeypot(port)
```

To run this script, save it to a file (e.g., `honeypot.py`) and execute it using Python. Replace the `port` value with the desired port number you want the honeypot to listen on. This script will create a listening socket on the specified port, and whenever a connection is made, it will log the connection details to a file named `honeypot_log.txt`.

*This is a basic example, and real-world honeypots require more advanced techniques and security measures to effectively capture and analyze malicious activity while minimizing the risk to your network.*


---


# Honeypot using Go

An example of a basic `TCP` honeypot using **Go**:

```go
package main

import (
	"fmt"
	"log"
	"net"
	"time"
)

func handleConnection(conn net.Conn) {
	addr := conn.RemoteAddr()
	fmt.Printf("[*] Connection from: %s at %s\n", addr, time.Now())

	// Log the connection details to a file
	logFile, err := openLogFile("honeypot_log.txt")
	if err != nil {
		log.Printf("Error opening log file: %v\n", err)
	} else {
		defer logFile.Close()
		log.Printf("Connection from: %s at %s\n", addr, time.Now())
	}

	conn.Close()
}

func openLogFile(filename string) (*os.File, error) {
	logFile, err := os.OpenFile(filename, os.O_WRONLY|os.O_APPEND|os.O_CREATE, 0644)
	if err != nil {
		return nil, err
	}
	return logFile, nil
}

func honeypot(port int) {
	listenAddr := fmt.Sprintf(":%d", port)
	listener, err := net.Listen("tcp", listenAddr)
	if err != nil {
		log.Fatalf("Error starting honeypot: %v", err)
	}
	defer listener.Close()

	fmt.Printf("[*] Listening on %s\n", listenAddr)

	for {
		conn, err := listener.Accept()
		if err != nil {
			log.Printf("Error accepting connection: %v\n", err)
			continue
		}
		go handleConnection(conn)
	}
}

func main() {
	port := 12345 // Change this to the desired port number
	honeypot(port)
}
```

Save this code to a `.go` file (e.g., `honeypot.go`) and then compile and run it using the Go compiler:

```bash
go run honeypot.go
```

Just like the previous Python example, this Go program creates a TCP honeypot that listens on a specified port. When a connection is made, it logs the connection details to a file named `honeypot_log.txt`.

*Remember that setting up a honeypot should be done with care, as it can attract malicious activity. Additionally, consider implementing more advanced features and security measures when creating a production-ready honeypot.*

---

# A slightly more Advanced Honeypot Setup using Docker

Creating an advanced honeypot involves a deep understanding of networking, security, and system administration. It's important to approach this responsibly, as honeypots can attract real attackers and potentially expose your systems to risks. Below is an example of a more advanced honeypot using Go and the Cowrie honeypot framework.

The Cowrie honeypot is a widely used open-source honeypot that emulates a SSH server, capturing SSH-based attacks and gathering valuable information about attacker behavior. It provides a more advanced and comprehensive solution compared to a simple TCP listener.

Here's how you can set up a basic Cowrie honeypot using Docker:

1. Install Docker on your system if you haven't already: https://docs.docker.com/get-docker/

2. Create a `docker-compose.yml` file with the following content:

```yaml
version: '3'
services:
  cowrie:
    image: cowrie/cowrie
    ports:
      - "2222:2222"
    volumes:
      - ./cowrie-data:/cowrie/cowrie-git/var
```

3. Create a directory named `cowrie-data` in the same location as your `docker-compose.yml` file. This directory will store the Cowrie honeypot data.

4. Open a terminal and navigate to the directory containing the `docker-compose.yml` file.

5. Run the following command to start the Cowrie honeypot:

```bash
docker-compose up -d
```

This command will download the **Cowrie Docker** image and start the honeypot container. It will listen on port `2222` for incoming SSH connections.

6. Monitor the honeypot logs and captured data using the `cowrie-data` directory.

Keep in mind that this is just a basic setup of the Cowrie honeypot using Docker. The Cowrie project provides advanced configuration options, including customizing the behavior of the honeypot, analyzing captured data, and setting up alerting systems.

*Remember to regularly update and monitor your honeypot setup, as attackers can evolve their techniques over time. Always prioritize security and ensure you're following legal guidelines when deploying and using a honeypot.*

---

# A slightly more Advanced Honeypot Setup using Podman

Podman is an alternative containerization tool to Docker. Here's how I set up the Cowrie honeypot using Podman:

1. Install Podman on your system if you haven't already: https://podman.io/getting-started/installation

2. Create a `docker-compose.yml` file with the following content:

```yaml
version: '3'
services:
  cowrie:
    image: cowrie/cowrie
    ports:
      - "2222:2222"
    volumes:
      - ./cowrie-data:/cowrie/cowrie-git/var
```

3. Create a directory named `cowrie-data` in the same location as your `docker-compose.yml` file. This directory will store the Cowrie honeypot data.

4. Open a terminal and navigate to the directory containing the `docker-compose.yml` file.

5. Run the following command to start the Cowrie honeypot using Podman:

```bash
podman-compose up -d
```

This command will download the Cowrie container image and start the honeypot container. It will listen on port `2222` for incoming SSH connections.

6. Monitor the honeypot logs and captured data using the `cowrie-data` directory.

Similar to Docker, Podman allows you to manage containers and interact with them using similar commands. The `podman-compose` tool is used as a replacement for `docker-compose` to manage multi-container applications.

*Always ensure you're following best practices for security and adhere to legal guidelines when deploying and using a honeypot, regardless of the containerization tool you choose.*

---

Documentation By: **Raymond C. TURNER**

**Last Updated:** Saturday 30th September 2023