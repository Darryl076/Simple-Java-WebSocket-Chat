# Simple Java WebSocket Chat

A minimal Java WebSocket chat application demonstrating the fundamentals of client-server communication using WebSockets.

This project is intentionally simple and is designed as a learning exercise rather than a production-ready chat application.

## Features

* Multiple clients can connect simultaneously.
* Users choose a display name when joining.
* Messages are broadcast to every connected client except the sender.
* Join notifications are broadcast to other users.
* Clients can disconnect gracefully by typing `bye`.
* Console-based interface with no GUI.

## Technologies Used

* Java 21+
* Java HTTP Client (`java.net.http.WebSocket`)
* Java-WebSocket library (server implementation)

---

# How It Works

## Server

The server listens on **port 8080** and waits for incoming WebSocket connections.

When a client connects:

1. The username is read from the connection URL.
2. The username is stored alongside the client's socket address.
3. Other connected users are notified that someone joined.

When a client sends a message:

1. The sender's username is looked up.
2. The message is formatted as:

```
Username: Message
```

3. The message is broadcast to every connected client except the sender.

When the server starts it prints:

```
Server listening on Port: 8080
```

---

## Client

Each client:

1. Prompts the user for a name.
2. Connects to the WebSocket server.
3. Listens for incoming chat messages.
4. Sends any text entered into the console.

Typing

```
bye
```

closes the connection normally.

---

# Running the Project

## 1. Start the Server

Run:

```
SimpleWebSocketServer
```

The server begins listening on:

```
ws://localhost:8080
```

---

## 2. Start One or More Clients

Run:

```
WebSocketClient
```

Enter a username when prompted.

Example:

```
Enter your name to join chat:
Alice
```

Start another client and join with a different name.

---

## Example Session

Client 1

```
Enter your name to join chat:
Alice
```

Client 2

```
Enter your name to join chat:
Bob
```

Bob will receive:

```
Alice joined
```

Alice types:

```
Hello everyone!
```

Bob sees:

```
Alice: Hello everyone!
```

If Alice types:

```
bye
```

the client disconnects gracefully.

---

# Project Structure

```
SimpleWebSocketServer.java
    WebSocket server
    Handles connections
    Stores usernames
    Broadcasts messages

WebSocketClient.java
    Console chat client
    Connects to the server
    Sends and receives messages
```

---

# Limitations

This project intentionally keeps the implementation simple.

Current limitations include:

* Usernames are not validated.
* Duplicate usernames are allowed.
* Users leaving are not announced.
* No authentication or encryption.
* No message history.
* No private messaging.
* User mapping is stored only in memory.
* Intended for local network or learning purposes.

---

# Learning Objectives

This project demonstrates:

* Creating a WebSocket server
* Connecting with Java's built-in HTTP WebSocket client
* Receiving asynchronous messages
* Broadcasting messages to multiple clients
* Managing connected users
* Gracefully closing WebSocket connections

It provides a foundation that can later be extended with features such as authentication, chat rooms, persistent storage, GUI clients, or secure (`wss://`) connections.
