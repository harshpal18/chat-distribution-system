Here is a clean, professional **README.md** for your chat client script.
It includes description, features, usage, and troubleshooting.

---

# 🗨️ ChatApp – Python Socket Chat Client

A lightweight, terminal-based chat client built using **Python sockets** and **threading**.
This client connects to a chat server and enables real-time messaging between multiple users.

---

## 🚀 Features

* Connects to a TCP chat server
* Handles messaging in **two parallel threads**:

  * `receive()` → continuously listens for messages
  * `write()` → lets the user type messages without interruptions
* Automatic username prompt from server

  * Defaults to `Guest<timestamp>` if blank
* Graceful shutdown using `/quit` or **Ctrl + C**
* Helpful error messages and reconnection hints
* Supports custom server IP/Port

---

## 📦 Requirements

* **Python 3.7+**
* No external libraries required

---

## 📁 File Structure

```
chat_client.py
README.md
```

*(Assuming you create the README with this content.)*

---

## ▶️ How to Run

### Default connection (localhost:5555)

```bash
python chat_client.py
```

### Connect to a custom server

```bash
python chat_client.py <host> <port>
```

Example:

```bash
python chat_client.py 192.168.1.100 5555
```

---

## 📝 Commands

| Command   | Description                                       |
| --------- | ------------------------------------------------- |
| **/quit** | Disconnects from the server and closes the client |

---

## ⚙️ How It Works

### 1. **Connection Setup**

The client attempts to connect to the server at the given host and port.
If successful, two threads start automatically:

* **Receive thread** → listens for incoming messages
* **Write thread** → accepts user input

### 2. **Username Handling**

When the server sends:

```
USERNAME|<prompt>
```

The client displays the prompt and asks you to enter a username.

If left empty, the client assigns:

```
Guest<timestamp>
```

### 3. **Graceful Exit**

The client safely closes the socket on:

* `/quit` command
* Keyboard interrupt (`CTRL + C`)
* Server disconnection

---

## ❗ Error Messages Explained

| Error                      | Meaning / Fix                              |
| -------------------------- | ------------------------------------------ |
| **ConnectionRefusedError** | Server is offline → Start the server first |
| **socket.gaierror**        | Invalid host/IP → Check address            |
| **ConnectionResetError**   | Server crashed or closed suddenly          |
| **Port must be a number**  | You typed an invalid port                  |

---

## 🛠️ Example Server (Optional)

If you need a server to test with, here’s a simple reference name:

```
chat_server.py
```

Run it first:

```bash
python chat_server.py
```

Then start the client.

---

AUTHOR : HARSH PAL (VIT BHOPAL)
