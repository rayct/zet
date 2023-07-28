# Upcoming Project - August 2023

## URL Shortener Microservice 

A simple URL shortner project witten in 5 different programming languages purely for comparison and performance measuring.

## Possible Languages Shortlist
    * GO
    * Python
    * C
    * JavaScript
    * TypeScript

### Go
Creating a full-fledged URL shortener is a complex task that involves handling database storage, HTTP server, and redirect logic. For the purpose of this example, I'll provide a simplified implementation of a URL shortener using Golang. This example will use an in-memory map as a simple database, but in a real-world scenario, you'd want to use a more robust database like MySQL or PostgreSQL.

Ensure you have Golang installed on your system before proceeding.

Let's start by creating a basic URL shortener:

1. First, create a new directory for your project and navigate to it:

```bash
mkdir url_shortener
cd url_shortener
```

2. Create the main Go file `main.go` with the following code:

```go
package main

import (
	"fmt"
	"log"
	"net/http"
	"sync"
)

var (
	shortToLongMap = make(map[string]string)
	longToShortMap = make(map[string]string)
	mutex          = &sync.Mutex{}
)

func generateShortURL() string {
	// In a real-world scenario, you would implement a proper algorithm to generate short URLs.
	// For simplicity, this example uses a basic counter-based approach.
	mutex.Lock()
	defer mutex.Unlock()
	shortURL := fmt.Sprintf("short%d", len(shortToLongMap)+1)
	return shortURL
}

func shortenURL(w http.ResponseWriter, r *http.Request) {
	if r.Method != http.MethodPost {
		http.Error(w, "Method not allowed", http.StatusMethodNotAllowed)
		return
	}

	longURL := r.FormValue("url")
	if longURL == "" {
		http.Error(w, "URL parameter is missing", http.StatusBadRequest)
		return
	}

	shortURL := generateShortURL()

	mutex.Lock()
	shortToLongMap[shortURL] = longURL
	longToShortMap[longURL] = shortURL
	mutex.Unlock()

	fmt.Fprintf(w, "Shortened URL: http://localhost:8080/%s", shortURL)
}

func redirectURL(w http.ResponseWriter, r *http.Request) {
	shortURL := r.URL.Path[1:]
	longURL, ok := shortToLongMap[shortURL]
	if !ok {
		http.NotFound(w, r)
		return
	}

	http.Redirect(w, r, longURL, http.StatusSeeOther)
}

func main() {
	http.HandleFunc("/shorten", shortenURL)
	http.HandleFunc("/", redirectURL)

	fmt.Println("Server started at http://localhost:8080")
	log.Fatal(http.ListenAndServe(":8080", nil))
}
```

3. Save the `main.go` file, and now you can run the URL shortener server:

```bash
go run main.go
```

Your server should be running now. You can access it at `http://localhost:8080`.

4. To test the URL shortener, you can use `curl` or any HTTP client. For example:

```bash
curl -X POST -d "url=https://www.example.com" http://localhost:8080/shorten
```

This should return a shortened URL, which you can then use to redirect to the original URL. When you visit the shortened URL, it should redirect you to the original URL.

Remember that this is a basic implementation and doesn't handle scalability, persistence, or potential security concerns. In a real-world scenario, you'd need to consider those aspects and possibly use a production-ready database and authentication mechanisms.


### Pyhon
Sure, I can provide you with the equivalent Python code for the URL shortener example. The Python version will use the Flask framework to create a simple web server for handling the URL shortening and redirection.

Before proceeding, make sure you have Python and Flask installed on your system.

1. Create a new directory for your project and navigate to it:

2. Create a new Python file `app.py` with the following code:

```python
from flask import Flask, request, redirect, jsonify
import random
import string

app = Flask(__name__)

short_to_long_map = {}
long_to_short_map = {}


def generate_short_url():
    # In a real-world scenario, you would implement a proper algorithm to generate short URLs.
    # For simplicity, this example uses a basic random string approach.
    characters = string.ascii_letters + string.digits
    short_url = ''.join(random.choice(characters) for _ in range(6))
    return short_url


@app.route('/shorten', methods=['POST'])
def shorten_url():
    long_url = request.form.get('url')
    if not long_url:
        return jsonify({"error": "URL parameter is missing"}), 400

    short_url = generate_short_url()

    short_to_long_map[short_url] = long_url
    long_to_short_map[long_url] = short_url

    return jsonify({"shortened_url": f"http://localhost:5000/{short_url}"}), 200


@app.route('/<short_url>', methods=['GET'])
def redirect_url(short_url):
    long_url = short_to_long_map.get(short_url)
    if not long_url:
        return jsonify({"error": "Short URL not found"}), 404

    return redirect(long_url, code=302)


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

3. Save the `app.py` file, and now you can run the URL shortener server:

```bash
python app.py
```

Your server should be running now. You can access it at `http://localhost:5000`.

4. To test the URL shortener, you can use `curl` or any HTTP client. For example:

```bash
curl -X POST -d "url=https://www.example.com" http://localhost:5000/shorten
```

This should return a shortened URL, which you can then use to redirect to the original URL. When you visit the shortened URL, it should redirect you to the original URL.

Just like the Go implementation, this Python version is a basic example and lacks advanced features like scalability, persistence, or security. In a real-world scenario, you'd need to consider those aspects and possibly use a production-ready database and authentication mechanisms.


### C
Sure! Converting the URL shortener example to C involves using a C web framework or library to handle HTTP requests and responses. One popular option for this purpose is `libmicrohttpd`, which provides a small, lightweight, and embeddable HTTP server.

Before proceeding, make sure you have `libmicrohttpd` installed on your system.

Here's the C implementation of the URL shortener:

1. Create a new directory for your project and navigate to it.

2. Create a new C file, for example, `main.c`, with the following code:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <microhttpd.h>

struct ShortURL {
    char short_url[7];
    char long_url[200];
};

struct ShortURL short_urls[100];
int num_short_urls = 0;

const char* generate_short_url() {
    // In a real-world scenario, you would implement a proper algorithm to generate short URLs.
    // For simplicity, this example uses a basic random string approach.
    const char characters[] = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    char short_url[7];
    for (int i = 0; i < 6; i++) {
        short_url[i] = characters[rand() % (sizeof(characters) - 1)];
    }
    short_url[6] = '\0';
    return strdup(short_url);
}

static int shorten_url_callback(void* cls, struct MHD_Connection* connection,
                                const char* url, const char* method,
                                const char* version, const char* upload_data,
                                size_t* upload_data_size, void** ptr) {
    if (*ptr == NULL) {
        *ptr = (void*)1;
        return MHD_YES;
    }

    if (strcmp(method, "POST") != 0) {
        const char* response = "Method not allowed\n";
        struct MHD_Response* resp = MHD_create_response_from_buffer(strlen(response), (void*)response, MHD_RESPMEM_PERSISTENT);
        int ret = MHD_queue_response(connection, MHD_HTTP_METHOD_NOT_ALLOWED, resp);
        MHD_destroy_response(resp);
        return ret;
    }

    const char* long_url = MHD_lookup_connection_value(connection, MHD_GET_ARGUMENT_KIND, "url");
    if (long_url == NULL) {
        const char* response = "URL parameter is missing\n";
        struct MHD_Response* resp = MHD_create_response_from_buffer(strlen(response), (void*)response, MHD_RESPMEM_PERSISTENT);
        int ret = MHD_queue_response(connection, MHD_HTTP_BAD_REQUEST, resp);
        MHD_destroy_response(resp);
        return ret;
    }

    if (num_short_urls >= 100) {
        const char* response = "Server capacity exceeded\n";
        struct MHD_Response* resp = MHD_create_response_from_buffer(strlen(response), (void*)response, MHD_RESPMEM_PERSISTENT);
        int ret = MHD_queue_response(connection, MHD_HTTP_INTERNAL_SERVER_ERROR, resp);
        MHD_destroy_response(resp);
        return ret;
    }

    const char* short_url = generate_short_url();

    strncpy(short_urls[num_short_urls].short_url, short_url, sizeof(short_urls[num_short_urls].short_url));
    strncpy(short_urls[num_short_urls].long_url, long_url, sizeof(short_urls[num_short_urls].long_url));
    num_short_urls++;

    const char* response_template = "Shortened URL: http://localhost:8080/%s\n";
    char response[200];
    snprintf(response, sizeof(response), response_template, short_url);

    struct MHD_Response* resp = MHD_create_response_from_buffer(strlen(response), (void*)response, MHD_RESPMEM_MUST_FREE);
    int ret = MHD_queue_response(connection, MHD_HTTP_OK, resp);
    MHD_destroy_response(resp);
    return ret;
}

static int redirect_url_callback(void* cls, struct MHD_Connection* connection,
                                 const char* url, const char* method,
                                 const char* version, const char* upload_data,
                                 size_t* upload_data_size, void** ptr) {
    if (*ptr == NULL) {
        *ptr = (void*)1;
        return MHD_YES;
    }

    char short_url[7];
    sscanf(url, "/%s", short_url);

    char* long_url = NULL;
    for (int i = 0; i < num_short_urls; i++) {
        if (strcmp(short_urls[i].short_url, short_url) == 0) {
            long_url = short_urls[i].long_url;
            break;
        }
    }

    if (long_url == NULL) {
        const char* response = "Short URL not found\n";
        struct MHD_Response* resp = MHD_create_response_from_buffer(strlen(response), (void*)response, MHD_RESPMEM_PERSISTENT);
        int ret = MHD_queue_response(connection, MHD_HTTP_NOT_FOUND, resp);
        MHD_destroy_response(resp);
        return ret;
    }

    struct MHD_Response* resp = MHD_create_response_from_buffer(0, NULL, MHD_RESPMEM_PERSISTENT);
    int ret = MHD_queue_response(connection, MHD_HTTP_SEE_OTHER, resp);
    MHD_add_response_header(resp, "Location", long_url);
    MHD_destroy_response(resp);
    return ret;
}

int main() {
    struct MHD_Daemon* daemon = MHD_start_daemon(MHD_USE_SELECT_INTERNALLY, 8080, NULL, NULL,
                                                &shorten_url_callback, NULL, MHD_OPTION_END);
    if (daemon == NULL) {
        printf("Failed to start HTTP server.\n");
        return 1;
    }

    printf("Server started at http://localhost:8080\n");

    getchar();

    MHD_stop_daemon(daemon);
    return 0;
}
```

3. Save the `main.c` file, and now you can compile the C program. If you're using GCC, you can compile it like this:

```bash
gcc -o url_shortener main.c -lmicrohttpd
```

4. Run the compiled C program:

```bash
./url_shortener
```

Your server should be running now. You can access it at `http://localhost:8080`.

To test the URL shortener, you can use `curl` or any HTTP client. For example:

```bash
curl -X POST -d "url=https://www.example.com" http://localhost:8080/shorten
```

This should return a shortened URL, which you can then use to redirect to the original URL. When you visit the shortened URL, it should redirect you to the original URL.

As with the previous implementations, this C version is a basic example and lacks advanced features like scalability, persistence, or security. In a real-world scenario, you'd need to consider those aspects and possibly use a production-ready HTTP server and database library.


### JavaScript
Certainly! Converting the URL shortener example to JavaScript involves using a web framework or library for handling HTTP requests and responses. For this example, we'll use Node.js with the Express framework.

Make sure you have Node.js installed on your system before proceeding.

Here's the JavaScript implementation of the URL shortener:

1. Create a new directory for your project and navigate to it.

2. Initialize a new Node.js project and install the required dependencies:

```bash
npm init -y
npm install express body-parser
```

3. Create a new JavaScript file, for example, `app.js`, with the following code:

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const crypto = require('crypto');

const app = express();
const port = 8080;

app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

const shortToLongMap = {};
const longToShortMap = {};

function generateShortURL() {
  // In a real-world scenario, you would implement a proper algorithm to generate short URLs.
  // For simplicity, this example uses a basic random string approach.
  const characters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
  let shortURL = '';
  for (let i = 0; i < 6; i++) {
    const randomIndex = crypto.randomInt(characters.length);
    shortURL += characters.charAt(randomIndex);
  }
  return shortURL;
}

app.post('/shorten', (req, res) => {
  const longURL = req.body.url;
  if (!longURL) {
    return res.status(400).json({ error: 'URL parameter is missing' });
  }

  const shortURL = generateShortURL();

  shortToLongMap[shortURL] = longURL;
  longToShortMap[longURL] = shortURL;

  const response = `Shortened URL: http://localhost:${port}/${shortURL}`;
  res.status(200).json({ shortened_url: response });
});

app.get('/:shortURL', (req, res) => {
  const longURL = shortToLongMap[req.params.shortURL];
  if (!longURL) {
    return res.status(404).json({ error: 'Short URL not found' });
  }
  res.redirect(302, longURL);
});

app.listen(port, () => {
  console.log(`Server started at http://localhost:${port}`);
});
```

4. Save the `app.js` file.

5. Run the Node.js server:

```bash
node app.js
```

Your server should be running now. You can access it at `http://localhost:8080`.

6. To test the URL shortener, you can use `curl` or any HTTP client. For example:

```bash
curl -X POST -d "url=https://www.example.com" http://localhost:8080/shorten
```

This should return a shortened URL, which you can then use to redirect to the original URL. When you visit the shortened URL, it should redirect you to the original URL.

As with the previous implementations, this JavaScript version is a basic example and lacks advanced features like scalability, persistence, or security. In a real-world scenario, you'd need to consider those aspects and possibly use a production-ready web server and database.

### TypeScript
Sure! Converting the URL shortener example to TypeScript involves using Node.js with the Express framework to create a web server for handling the URL shortening and redirection.

Before proceeding, make sure you have Node.js and npm installed on your system.

Here's the TypeScript implementation of the URL shortener:

1. Create a new directory for your project and navigate to it.

2. Initialize a new Node.js project and install the necessary dependencies:

```bash
npm init -y
npm install express body-parser --save
npm install @types/express @types/body-parser --save-dev
```

3. Create a new TypeScript file, for example, `app.ts`, with the following code:

```typescript
import express, { Request, Response } from 'express';
import bodyParser from 'body-parser';

const app = express();
const PORT = 5000;

interface ShortURL {
  shortURL: string;
  longURL: string;
}

const shortURLs: ShortURL[] = [];

function generateShortURL(): string {
  // In a real-world scenario, you would implement a proper algorithm to generate short URLs.
  // For simplicity, this example uses a basic random string approach.
  const characters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
  let shortURL = '';
  for (let i = 0; i < 6; i++) {
    const randomIndex = Math.floor(Math.random() * characters.length);
    shortURL += characters.charAt(randomIndex);
  }
  return shortURL;
}

app.use(bodyParser.urlencoded({ extended: false }));

app.post('/shorten', (req: Request, res: Response) => {
  const longURL = req.body.url;
  if (!longURL) {
    return res.status(400).json({ error: 'URL parameter is missing' });
  }

  if (shortURLs.length >= 100) {
    return res.status(500).json({ error: 'Server capacity exceeded' });
  }

  const shortURL = generateShortURL();
  shortURLs.push({ shortURL, longURL });

  res.json({ shortenedURL: `http://localhost:${PORT}/${shortURL}` });
});

app.get('/:shortURL', (req: Request, res: Response) => {
  const shortURL = req.params.shortURL;
  const foundURL = shortURLs.find((entry) => entry.shortURL === shortURL);

  if (!foundURL) {
    return res.status(404).json({ error: 'Short URL not found' });
  }

  res.redirect(foundURL.longURL);
});

app.listen(PORT, () => {
  console.log(`Server started at http://localhost:${PORT}`);
});
```

4. Compile the TypeScript code to JavaScript:

```bash
npx tsc
```

This will create a `dist` folder with the transpiled JavaScript files.

5. Run the server:

```bash
node dist/app.js
```

Your server should be running now. You can access it at `http://localhost:5000`.

To test the URL shortener, you can use `curl` or any HTTP client. For example:

```bash
curl -X POST -d "url=https://www.example.com" http://localhost:5000/shorten
```

This should return a shortened URL, which you can then use to redirect to the original URL. When you visit the shortened URL, it should redirect you to the original URL.

As with the previous implementations, this TypeScript version is a basic example and lacks advanced features like scalability, persistence, or security. In a real-world scenario, you'd need to consider those aspects and possibly use a production-ready HTTP server and database library.


## SQL Database

Creating a SQL database requires selecting a specific database management system (DBMS) and then executing SQL commands to define and create the database structure. Below, I'll provide an example of creating a simple URL database using MySQL as the DBMS.

Assumptions:
- You have MySQL installed and set up on your system.
- You have a basic understanding of SQL.

1. Connect to MySQL:
First, you need to connect to your MySQL server using a client like MySQL Command Line Client or a graphical interface like MySQL Workbench.

2. Create a new database:
Let's assume we want to call our database "url_db."

```sql
CREATE DATABASE url_db;
```

3. Switch to the new database:
```sql
USE url_db;
```

4. Create a table to store URLs:
```sql
CREATE TABLE urls (
    id INT AUTO_INCREMENT PRIMARY KEY,
    url VARCHAR(255) NOT NULL,
    title VARCHAR(100),
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

This table will have the following columns:
- `id`: An auto-incrementing unique identifier for each URL.
- `url`: The URL itself, stored as a string of maximum length 255 characters.
- `title`: An optional column to store the title of the URL.
- `description`: An optional column to store a longer description or notes about the URL.
- `created_at`: A timestamp that automatically records the creation time of each entry.

5. Insert data into the table:
You can insert URLs into the table as follows:

```sql
INSERT INTO urls (url, title, description) VALUES
('https://www.example.com', 'Example Website', 'This is an example website.'),
('https://www.example2.com', 'Another Example', 'Another example URL.');
```

6. Query the data:
You can query the data in the table to retrieve stored URLs or perform other operations:

```sql
-- Retrieve all URLs in the table
SELECT * FROM urls;

-- Retrieve URLs with specific conditions
SELECT * FROM urls WHERE title LIKE '%example%';

-- Update a URL's title
UPDATE urls SET title = 'Updated Title' WHERE id = 1;

-- Delete a URL from the table
DELETE FROM urls WHERE id = 2;
```

Remember, this is a basic example to get you started. Depending on your specific needs and requirements, you might want to add more features or data validation to the database schema. Additionally, always ensure to take security measures like sanitizing user input and using parameterized queries to prevent SQL injection attacks.

### Create the API

To create an API that allows retrieving stored URLs, you'll need to set up a server with an API endpoint that interacts with the database. Below is a simple example of how you can create a RESTful API using Python and Flask, assuming you already have the MySQL database set up with the "urls" table as described in the previous answer.

Make sure you have the Flask and MySQL Connector Python packages installed. You can install them using pip:

```bash
pip install Flask mysql-connector-python
```

Now, let's create the API:

```python
from flask import Flask, jsonify
import mysql.connector

app = Flask(__name__)

# MySQL configurations
db_config = {
    'host': 'localhost',
    'user': 'your_username',
    'password': 'your_password',
    'database': 'url_db',
}

# Endpoint to retrieve all URLs
@app.route('/api/urls', methods=['GET'])
def get_urls():
    try:
        # Connect to the database
        connection = mysql.connector.connect(**db_config)
        cursor = connection.cursor()

        # Fetch all URLs from the 'urls' table
        query = "SELECT id, url, title, description, created_at FROM urls"
        cursor.execute(query)
        urls = cursor.fetchall()

        # Convert the results to a list of dictionaries
        url_list = []
        for url in urls:
            url_data = {
                'id': url[0],
                'url': url[1],
                'title': url[2],
                'description': url[3],
                'created_at': url[4].isoformat(),  # Convert timestamp to ISO format
            }
            url_list.append(url_data)

        cursor.close()
        connection.close()

        # Return the URLs as JSON response
        return jsonify(url_list)

    except Exception as e:
        return jsonify({'error': str(e)}), 500

if __name__ == '__main__':
    app.run(debug=True)
```

Replace `'your_username'` and `'your_password'` with your MySQL username and password, respectively. Also, ensure that the database configurations (`db_config`) match your MySQL setup.

Save the above code in a Python file (e.g., `app.py`). Then, run the script:

```bash
python app.py
```

The API will be accessible at `http://127.0.0.1:5000/api/urls` by default.

Now, when you send a GET request to `http://127.0.0.1:5000/api/urls`, it will return a JSON response containing all the stored URLs along with their respective details. You can use this API to fetch the URLs and integrate it with your frontend or any other application that needs to retrieve the stored URLs.


### Convert API to URL 

To convert the API into a URL shortener, you'll need to add functionality to generate short URLs and handle the redirection from the short URL to the original long URL. We'll use a simple method to generate short URLs using a hash function (e.g., MD5 or SHA256) and store the mappings in the database.

Let's modify the API code to create a URL shortener:

```python
import hashlib
import base64

# ... Previous code ...

# Endpoint to create a short URL
@app.route('/api/shorten', methods=['POST'])
def shorten_url():
    try:
        # Get the long URL from the request
        data = request.get_json()
        long_url = data.get('long_url')

        if not long_url:
            return jsonify({'error': 'Missing long_url parameter.'}), 400

        # Generate a hash of the long URL to create a unique short key
        md5_hash = hashlib.md5(long_url.encode()).digest()
        short_key = base64.urlsafe_b64encode(md5_hash)[:8].decode()

        # Connect to the database
        connection = mysql.connector.connect(**db_config)
        cursor = connection.cursor()

        # Check if the short key already exists in the database
        query = "SELECT id FROM urls WHERE short_key = %s"
        cursor.execute(query, (short_key,))
        result = cursor.fetchone()

        if result:
            # Short key already exists, return existing short URL
            cursor.close()
            connection.close()
            return jsonify({'short_url': f"http://127.0.0.1:5000/{short_key}"}), 200

        # Insert the short URL into the 'urls' table
        query = "INSERT INTO urls (url, short_key) VALUES (%s, %s)"
        cursor.execute(query, (long_url, short_key))
        connection.commit()

        cursor.close()
        connection.close()

        # Return the newly created short URL
        return jsonify({'short_url': f"http://127.0.0.1:5000/{short_key}"}), 201

    except Exception as e:
        return jsonify({'error': str(e)}), 500

# Endpoint to redirect to the original long URL from the short URL
@app.route('/<short_key>', methods=['GET'])
def redirect_to_long_url(short_key):
    try:
        # Connect to the database
        connection = mysql.connector.connect(**db_config)
        cursor = connection.cursor()

        # Retrieve the original long URL from the 'urls' table based on the short key
        query = "SELECT url FROM urls WHERE short_key = %s"
        cursor.execute(query, (short_key,))
        result = cursor.fetchone()

        if not result:
            # Short key not found, return an error or redirect to a default page
            cursor.close()
            connection.close()
            return jsonify({'error': 'Short URL not found.'}), 404

        long_url = result[0]

        cursor.close()
        connection.close()

        # Redirect to the original long URL
        return redirect(long_url, code=302)

    except Exception as e:
        return jsonify({'error': str(e)}), 500

# ... Rest of the code ...
```

In this code, we've added two new endpoints:

1. `/api/shorten` (POST): This endpoint receives a JSON object with a "long_url" parameter and generates a short URL for it. It checks if the short key already exists in the database to avoid duplications.

2. `/<short_key>` (GET): This is a dynamic endpoint that handles redirection. When a user accesses `http://127.0.0.1:5000/<short_key>`, it looks up the original long URL associated with the short key and performs a temporary redirect (HTTP 302) to the original URL.

Note that this is a basic URL shortener implementation. For a production-grade system, you should consider additional features like custom short URLs, analytics, and security measures to prevent abuse or unauthorized access.