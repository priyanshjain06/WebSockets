# HTTP

**Request–response protocol**

- Client initiates every communication
- Server cannot push data on its own

---

# WebSocket

**Full-duplex, persistent communication protocol**

- Client and server can send data anytime
- Designed for real-time communication

## Comparison Table

| Feature         | HTTP                    | WebSocket    |
| --------------- | ----------------------- | ------------ |
| Client → Server | Yes                     | Yes          |
| Server → Client | ❌ (only after request) | ✅ (anytime) |
| Real-time push  | ❌                      | ✅           |

> **Remember** → Server can also send data when there is a request by server, not in case of websocket (like insta notification, client does not send a request for notification but server sends notification in real-time!!)
>
> **Examples:** stock market, real time dashboard and WebRTC!

---

# Socket.io

## Core Concepts

- **Socket** → Individual users (client), each in a unique room with a unique ID
- **io** → All sockets (all users) in 1 single bigger room (Encapsulated)
- **Emit** → Trigger an event where data of the event is sent
- **On** → Receive the data (event), like an event listener handler

## Flow

| Client                                   | Server                        |
| ---------------------------------------- | ----------------------------- |
| `socket.on(Event, (message) => { ... })` | `io.emit(Event, "Hi")`        |
| `socket.emit("btn", 4)`                  | `socket.on("btn", () => {})` |

---

## Broadcasting

**Broadcast** → Send to everyone **EXCEPT** sender
```javascript
socket.broadcast.emit()
```

Sends to all except sender

---

## Targeting Specific Rooms

**to** → A socket wants to send message to socket B (Each socket has its unique ID room!)

**Example:**
```javascript
io.to("room1").emit("msg", "Hello room")
```

It is used for private messaging

---

## Joining Rooms

**Join** → Add a socket to a room (Creating group chat where all sockets (users or clients) are in a single room instead of individual unique rooms and IDs)

**Example:**
```javascript
socket.join("room1")
```

**Meaning:**

- This socket is now a member of `room1`
- A socket can join multiple rooms

---

## Method Summary

| Method                             | What it does                    |
| ---------------------------------- | ------------------------------- |
| `socket.join(room)`                | Adds socket to room             |
| `io.to(room).emit()`               | Sends to room (includes sender) |
| `socket.broadcast.emit()`          | Sends to all except sender      |
| `socket.broadcast.to(room).emit()` | Sends to room except sender     |

> **Note:** Rooms means logical connectivity, not physical connectivity!

---

## Real-World Mapping

| Feature     | Uses                                     |
| ----------- | ---------------------------------------- |
| `join`      | User joins chat room / video call        |
| `to`        | Send message to specific chat            |
| `broadcast` | Notify others about typing, join, leave |