# Create a simple intrusion detection system.

## Python

1. Go script for the intrusion detection system intrusion_detection.go
```yaml
2023-07-19 12:34:56 192.168.0.101 failed login attempt
2023-07-19 12:35:02 192.168.0.101 failed login attempt
2023-07-19 12:36:45 192.168.0.102 failed login attempt
2023-07-19 12:36:50 192.168.0.101 failed login attempt
2023-07-19 12:37:10 192.168.0.101 failed login attempt

```

1. Go script for the intrusion detection system intrusion_detection.go

```python
import time

def read_log_file(log_file):
    with open(log_file, 'r') as file:
        return file.readlines()

def detect_intrusion(log_entries, max_attempts=3, time_window=60):
    ip_attempts = {}
    for entry in log_entries:
        parts = entry.split()
        if len(parts) >= 5 and parts[-2] == 'failed' and parts[-1] == 'attempt':
            timestamp, _, ip_address, _ = parts[:4]
            timestamp = time.mktime(time.strptime(timestamp, '%Y-%m-%d %H:%M:%S'))
            if ip_address in ip_attempts:
                if timestamp - ip_attempts[ip_address][-1] <= time_window:
                    ip_attempts[ip_address].append(timestamp)
                    if len(ip_attempts[ip_address]) >= max_attempts:
                        return True, ip_address
                else:
                    ip_attempts[ip_address] = [timestamp]
            else:
                ip_attempts[ip_address] = [timestamp]
    return False, None

if __name__ == "__main__":
    log_file = "sample_log.txt"
    log_entries = read_log_file(log_file)
    intrusion_detected, suspicious_ip = detect_intrusion(log_entries)

    if intrusion_detected:
        print(f"Intrusion detected from {suspicious_ip}.")
    else:
        print("No intrusion detected.")

```

## Go

1. First, create a sample log file sample_log.txt with entries like the following:

```yaml
2023-07-19 12:34:56 192.168.0.101 failed login attempt
2023-07-19 12:35:02 192.168.0.101 failed login attempt
2023-07-19 12:36:45 192.168.0.102 failed login attempt
2023-07-19 12:36:50 192.168.0.101 failed login attempt
2023-07-19 12:37:10 192.168.0.101 failed login attempt

```

1. Go script for the intrusion detection system intrusion_detection.go

```go
    package main

import (
    "bufio"
    "fmt"
    "os"
    "strings"
    "time"
)

func readLogFile(logFile string) ([]string, error) {
    file, err := os.Open(logFile)
    if err != nil {
        return nil, err
    }
    defer file.Close()

    var logEntries []string
    scanner := bufio.NewScanner(file)
    for scanner.Scan() {
        logEntries = append(logEntries, scanner.Text())
    }
    return logEntries, scanner.Err()
}

func detectIntrusion(logEntries []string, maxAttempts int, timeWindow time.Duration) (bool, string) {
    ipAttempts := make(map[string][]time.Time)

    for _, entry := range logEntries {
        parts := strings.Fields(entry)
        if len(parts) >= 5 && parts[3] == "failed" && parts[4] == "login" && parts[5] == "attempt" {
            timestampStr := parts[0] + " " + parts[1]
            timestamp, err := time.Parse("2006-01-02 15:04:05", timestampStr)
            if err != nil {
                continue
            }

            ipAddress := parts[2]
            if attempts, ok := ipAttempts[ipAddress]; ok {
                if time.Since(attempts[len(attempts)-1]) <= timeWindow {
                    ipAttempts[ipAddress] = append(ipAttempts[ipAddress], timestamp)
                    if len(ipAttempts[ipAddress]) >= maxAttempts {
                        return true, ipAddress
                    }
                } else {
                    ipAttempts[ipAddress] = []time.Time{timestamp}
                }
            } else {
                ipAttempts[ipAddress] = []time.Time{timestamp}
            }
        }
    }

    return false, ""
}

func main() {
    logFile := "sample_log.txt"
    logEntries, err := readLogFile(logFile)
    if err != nil {
        fmt.Println("Error reading log file:", err)
        return
    }

    intrusionDetected, suspiciousIP := detectIntrusion(logEntries, 3, 60*time.Second)

    if intrusionDetected {
        fmt.Printf("Intrusion detected from %s.\n", suspiciousIP)
    } else {
        fmt.Println("No intrusion detected.")
    }
}

```

