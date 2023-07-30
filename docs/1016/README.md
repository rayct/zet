# URL Shortener Microservice 

**Upcoming Project - August 2023**

Creating a full-fledged URL shortener with a SQL database and API involves several components. For simplicity, I'll guide you through building a basic version using `Flask` as the web framework, `SQLite` as the database, and a `RESTful API` to interact with the URL shortener. Note! that this implementation is meant for learning purposes and may not be suitable for production use.


## Implementation 1 - Python
* Stack
    * Python
    * Flask
    * SQLite

### Install Flask
Before you begin, make sure you have Flask installed. If you don't have it, install it using:

```bash
pip install flask
```

Now, let's get started with building the URL shortener:

### Create a new Python file, e.g., `app.py`.

### Import the necessary libraries:

```python
from flask import Flask, request, jsonify, redirect, render_template
import string
import random
import sqlite3
```

### Initialize the Flask app:

```python
app = Flask(__name__)
app.config['BASE_URL'] = "http://yourdomain.com/"  # Replace with your domain
```

### Define functions for generating short URLs and storing them in the database:

```python
def generate_short_url():
    chars = string.ascii_letters + string.digits
    return ''.join(random.choice(chars) for _ in range(6))

def store_url(short_url, original_url):
    conn = sqlite3.connect('url_shortener.db')
    c = conn.cursor()
    c.execute("INSERT INTO urls (short_url, original_url) VALUES (?, ?)", (short_url, original_url))
    conn.commit()
    conn.close()
```

### Implement routes for handling the URL shortener:

```python
@app.route('/')
def index():
    return render_template('index.html')  # Create a basic HTML form to submit URLs

@app.route('/shorten', methods=['POST'])
def shorten_url():
    original_url = request.form['original_url']
    short_url = generate_short_url()
    store_url(short_url, original_url)
    return jsonify({'short_url': app.config['BASE_URL'] + short_url})

@app.route('/<short_url>')
def redirect_to_original_url(short_url):
    conn = sqlite3.connect('url_shortener.db')
    c = conn.cursor()
    c.execute("SELECT original_url FROM urls WHERE short_url=?", (short_url,))
    result = c.fetchone()
    conn.close()
    if result:
        original_url = result[0]
        return redirect(original_url)
    return "URL not found", 404
```

### Initialize the database:

```python
def initialize_database():
    conn = sqlite3.connect('url_shortener.db')
    c = conn.cursor()
    c.execute('''CREATE TABLE IF NOT EXISTS urls (
                    id INTEGER PRIMARY KEY AUTOINCREMENT,
                    short_url TEXT NOT NULL,
                    original_url TEXT NOT NULL
                  )''')
    conn.close()

if __name__ == '__main__':
    initialize_database()
    app.run(debug=True)
```

### Create a simple HTML template for the form. Save it as `index.html` in a folder named `templates`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>URL Shortener</title>
</head>
<body>
    <h1>URL Shortener</h1>
    <form method="post" action="/shorten">
        <label for="original_url">Enter your URL:</label>
        <input type="text" id="original_url" name="original_url" required>
        <button type="submit">Shorten</button>
    </form>
</body>
</html>
```

### Run the Flask app:

```bash
python app.py
```

Visit `http://127.0.0.1:5000/` in your browser, and you'll see a form where you can input your long URL. After submitting, the app will generate a short URL, store it in the database, and display it as a JSON response. When you visit the short URL, you will be redirected to the original long URL.

This implementation covers the basics of a URL shortener with a SQL database endpoint and API using Flask.

**NOTE!...** Keep in mind that in a real-world scenario, you'd need to add more robust error handling, user authentication, and possibly implement additional features for security and analytics.


## Implementation 2 - GO

* Stack
    * GO
    * Gorilla Mux Router
    * SQLite

Simple URL shortener in `Go (Golang).` We'll use the `Gorilla Mux router`for handling routes and the standard `"database/sql"` package to work with an `SQLite database.` Make sure you have `Go` installed and have set up your workspace properly.

### Create a new directory for your Go project and navigate into it.

### Initialize a new Go module:

```bash
go mod init urlshortener
```

### Install the required packages:

```bash
go get -u github.com/gorilla/mux
go get -u github.com/mattn/go-sqlite3
```

### Create a new Go file, e.g., `main.go`, and add the following code:

```go
package main

import (
    "database/sql"
    "fmt"
    "log"
    "math/rand"
    "net/http"
    "strings"
    "time"

    "github.com/gorilla/mux"
    _ "github.com/mattn/go-sqlite3"
)

const (
    charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
)

var baseURL = "http://yourdomain.com/" // Replace with your domain

func generateShortURL() string {
    rand.Seed(time.Now().UnixNano())
    b := make([]byte, 6)
    for i := range b {
        b[i] = charset[rand.Intn(len(charset))]
    }
    return string(b)
}

func storeURL(shortURL, originalURL string) {
    db, err := sql.Open("sqlite3", "url_shortener.db")
    if err != nil {
        log.Fatal(err)
    }
    defer db.Close()

    stmt, err := db.Prepare("INSERT INTO urls(short_url, original_url) VALUES(?, ?)")
    if err != nil {
        log.Fatal(err)
    }
    _, err = stmt.Exec(shortURL, originalURL)
    if err != nil {
        log.Fatal(err)
    }
}

func getOriginalURL(shortURL string) string {
    db, err := sql.Open("sqlite3", "url_shortener.db")
    if err != nil {
        log.Fatal(err)
    }
    defer db.Close()

    var originalURL string
    err = db.QueryRow("SELECT original_url FROM urls WHERE short_url = ?", shortURL).Scan(&originalURL)
    if err != nil {
        return ""
    }

    return originalURL
}

func indexHandler(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "text/html; charset=utf-8")
    fmt.Fprintf(w, `
    <!DOCTYPE html>
    <html>
    <head>
        <title>URL Shortener</title>
    </head>
    <body>
        <h1>URL Shortener</h1>
        <form method="post" action="/shorten">
            <label for="original_url">Enter your URL:</label>
            <input type="text" id="original_url" name="original_url" required>
            <button type="submit">Shorten</button>
        </form>
    </body>
    </html>
    `)
}

func shortenHandler(w http.ResponseWriter, r *http.Request) {
    r.ParseForm()
    originalURL := r.Form.Get("original_url")
    if originalURL == "" {
        http.Error(w, "Invalid request", http.StatusBadRequest)
        return
    }

    shortURL := generateShortURL()
    storeURL(shortURL, originalURL)
    response := map[string]string{"short_url": baseURL + shortURL}
    w.Header().Set("Content-Type", "application/json")
    http.Header.Add(w.Header(), "Access-Control-Allow-Origin", "*")
    fmt.Fprintf(w, `{"short_url": "%s"}`, baseURL+shortURL)
}

func redirectHandler(w http.ResponseWriter, r *http.Request) {
    vars := mux.Vars(r)
    shortURL := vars["shortURL"]
    originalURL := getOriginalURL(shortURL)
    if originalURL != "" {
        http.Redirect(w, r, originalURL, http.StatusMovedPermanently)
        return
    }
    http.NotFound(w, r)
}

func main() {
    db, err := sql.Open("sqlite3", "url_shortener.db")
    if err != nil {
        log.Fatal(err)
    }
    defer db.Close()

    _, err = db.Exec(`CREATE TABLE IF NOT EXISTS urls (
                        id INTEGER PRIMARY KEY AUTOINCREMENT,
                        short_url TEXT NOT NULL,
                        original_url TEXT NOT NULL
                      )`)
    if err != nil {
        log.Fatal(err)
    }

    r := mux.NewRouter()
    r.HandleFunc("/", indexHandler).Methods("GET")
    r.HandleFunc("/shorten", shortenHandler).Methods("POST")
    r.HandleFunc("/{shortURL}", redirectHandler).Methods("GET")

    fmt.Println("Starting server at :8080")
    log.Fatal(http.ListenAndServe(":8080", r))
}
```

### Run the Go application:

```bash
go run main.go
```

Now, visit `http://127.0.0.1:8080/` in your browser, and you'll see a form where you can input your long URL. After submitting, the app will generate a short URL, store it in the database, and display it as a JSON response. When you visit the short URL, you will be redirected to the original long URL.

**NOTE!...** Remember, this is a basic implementation, and in a real-world scenario, you'd need to add more robust error handling, user authentication, and possibly implement additional features for security and analytics.

**Documentation By:** `Raymond C. TURNER`