# Echoserver
Echo server and client using python socket
# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

HTML content creation is done

### Step 2:

Design of webserver workflow

### Step 3:

Implementation using Python code

### Step 4:

Serving the HTML pages.

### Step 5:

Testing the webserver

## PROGRAM:
server:
```python
import socket
HOST = '127.0.0.1' 
PORT = 65432 
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    print(f"Server started. Listening on {HOST}:{PORT}...")
    conn, addr = s.accept()
    with conn:
        print(f"Connected by {addr}")
        while True:
            data = conn.recv(1024)
            if not data:
                break
                conn.sendall(data)
```
client:                
```python
import socket
HOST = '127.0.0.1' 
PORT = 65432
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    while True:
        message = input("Enter message (or 'exit' to quit): ")
        if message.lower() == 'exit':
            break
        s.sendall(message.encode())
        data = s.recv(1024)
        print(f"Echo from server: {data.decode()}")
```
##  Architecture Diagram

```bash
+--------------------------+
|  User's Web Browser      |
|  (Client: Chrome/Firefox)|
+-----------+--------------+
            |
            |  HTTP Request (GET /)
            v
+-----------+--------------+
|   Python Web Server      |
| (http.server + Handler)  |
| - Listens on Port 8000   |
| - Handles GET Requests   |
| - Sends HTML Response    |
+-----------+--------------+
            |
            |  HTML Response
            v
+--------------------------+
|  User Sees Rendered Page |
|  <h1>Hello Web Server</h1>|
+--------------------------+
```


## OUTPUT:
<img width="1330" height="262" alt="Screenshot 2025-08-15 191026" src="https://github.com/user-attachments/assets/9bf492e3-5be8-41bd-848b-0abbb1cb80cb" />

## SERVER OUPTUT:
<img width="389" height="84" alt="Screenshot 2025-08-15 195107" src="https://github.com/user-attachments/assets/3c51a0fd-57b7-4c42-b177-2fa9725a9263" />

## CLIENT OUTPUT:
<img width="395" height="90" alt="Screenshot 2025-08-15 195111" src="https://github.com/user-attachments/assets/fc708c69-81fa-41f9-a189-f494c94ce140" />


## RESULT:
The program is executed succesfully.
