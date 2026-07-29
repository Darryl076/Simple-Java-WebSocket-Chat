# Simple Java WebSocket Chat

A basic console chat application written in Java to learn how WebSockets work.

## Features

* Multiple clients can connect.
* Users enter a name when joining.
* Messages are sent to every other connected client.
* Type `bye` to disconnect.

## Requirements

* Java 21+
* Java-WebSocket library (server)

## Running

1. Start `SimpleWebSocketServer`.
2. Run one or more `WebSocketClient` instances.
3. Enter a username.
4. Start chatting.

The server runs on:

```text
ws://localhost:8080
```

## Example

Client 1

```text
Enter your name to join chat:
Alice
```

Client 2

```text
Enter your name to join chat:
Bob
```

Bob sees:

```text
Alice joined
Alice: Hello!
```

## Purpose

This project was made to practice:

* WebSocket servers
* Java's built-in WebSocket client
* Sending and receiving messages
* Broadcasting to multiple clients

This is a learning project and does not include features like authentication, encryption, or message history.

