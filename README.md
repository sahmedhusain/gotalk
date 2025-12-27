# GoTalk 💬

[![Go](https://img.shields.io/badge/Go-1.20+-00ADD8?style=flat&logo=go)](https://golang.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE.md)

---

<p align="center">
  💬 <strong>GoTalk</strong><br/>
  <em>Real-time terminal chat powered by Go</em>
</p>

<p align="center">
  Concurrent TCP connections • Message broadcasting • Server-side logging
</p>

---

<p align="center">
  <strong>Real-time terminal chat powered by Go.</strong><br/>
  <em>Simple. Concurrent. Reliable.</em>
</p>

<!-- 🔗 Quick Navigation -->
<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-technologies-used">Tech Stack</a> •
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-how-to-use">Usage</a> •
  <a href="#-application-architecture">Architecture</a>
</p>

---

## Overview

**GoTalk** is a TCP-based chat server written in **Go** that allows multiple users to communicate in real time through their terminals. It supports concurrent connections, unique usernames, timestamped messages, and persistent chat logs.

Designed as a networking-focused project, GoTalk demonstrates core concepts such as TCP communication, goroutines, channels, and synchronized message broadcasting.

---

## ✨ Features

GoTalk includes the following core features:

- **Real-Time Messaging** 💬  
  Messages are delivered instantly to all connected users.

- **Unique Usernames** 👤  
  Each user must select a name that is not already in use.

- **Timestamps** ⏰  
  Every message includes the exact time it was sent.

- **Chat Logs** 📝  
  Messages and system events are stored in a log file for later review.

- **Concurrent Connections** 🔄  
  Handles up to 10 users simultaneously using goroutines.

- **Join / Leave Notifications** 🚪  
  Users are notified when someone enters or exits the chat.

- **Message History** 📜  
  Recent messages are displayed to users when they join.

---

## 🛠️ Technologies Used

- **Go** 🐹 – Core language, networking, and concurrency  
- **TCP/IP** 🌐 – Reliable communication protocol  
- **Goroutines** ⚡ – Concurrent client handling  
- **Channels** 📡 – Message broadcasting and synchronization  
- **File I/O** 💾 – Persistent chat logging  

<!-- 🧩 Technology Logo -->
<p align="center">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/go/go-original.svg" width="48"/>
</p>

---

## 🎯 Project Objective

GoTalk provides a minimal yet functional chat experience over TCP connections, focusing on reliability and concurrency.

### Core Responsibilities

1. **Users** – Manage connections and enforce unique usernames  
2. **Messages** – Broadcast messages with timestamps  
3. **Events** – Handle join and leave notifications  
4. **History** – Share recent messages with new users  

The application uses simple data structures combined with Go’s concurrency model to ensure smooth operation.

---

## 🚀 Getting Started

### Prerequisites

- Go version **1.20 or newer**
- A terminal to run the server and connect clients

### Installation & Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/sahmedhusain/gotalk.git
   ```

2. Navigate to the project directory:
   ```bash
   cd gotalk
   ```

3. Install dependencies:
   ```bash
   go mod tidy
   ```

4. Start the server:
   ```bash
   go run main.go
   ```

---

## 📖 How to Use

Run the server first. Then connect using a TCP client such as **Netcat**.  
The server listens on **localhost:8989** by default.

### Example Client Connection

```bash
nc localhost 8989
```

You will see the server welcome screen and be prompted to enter a username:

```text
Welcome to TCP-Chat!
         _nnnn_
        dGGGGMMb
       @p~qp~~qMb
       M|@||@) M|
       @,----.JM|
      JS^\__/  qKL
     dZP        qKRb
    dZP          qKKb
   fZP            SMMb
   HZM            MMMM
   FqM            MMMM
 __| ".        |\dS"qML
 |    `.       | `' \Zq
_)      \.___.,|     .'
\____   )MMMMMP|   .'
     `-'       `--'
[ENTER YOUR NAME]:
```

Enter a unique username (for example: `Alice`) to join the chat.

You will be prompted to enter a unique username before joining the chat.

---

## 💻 Terminal Examples

### Starting the Server

```bash
go run main.go
Server is running on Port :8989
```

### Chat Session Example

```text
[2024-10-12 15:12:45][system]: Alice joined the chat
[2024-10-12 15:13:02][Alice]: Hi Bob!
[2024-10-12 15:13:05][Bob]: Hello Alice!
```

### User Leaving

```text
[2024-10-12 15:14:00][system]: Bob has left our chat...
```

---

## 🛠️ Application Architecture

```text
┌───────────┐
│  Client   │
│ (Terminal)│
└─────┬─────┘
      │ TCP
┌─────▼─────┐
│  Server   │
│   (Go)    │
├───────────┤
│ Goroutine │──┐
│ Goroutine │  │ Broadcast
│ Goroutine │──┘ Channel
├───────────┤
│  Logger   │ → chat_logs.txt
└───────────┘
```

### Design Overview
- Each client runs in its own goroutine
- Messages flow through a central broadcast channel
- Chat activity is persisted using file-based logging

### Data Handling

- Each client connection runs in its own goroutine
- Messages are sent through a central broadcast channel

### Server-Side Design

- **Connections** – Dedicated goroutines per client  
- **Broadcasting** – Central message dispatcher  
- **Logging** – File-based event and message logs  
- **Concurrency Safety** – Locks prevent race conditions  
- **Error Handling** – Graceful disconnect handling  

### Networking

- TCP sockets ensure reliable delivery
- Channel-based broadcasting improves performance
- Connection limits prevent overload

---

## 📋 Chat System Details

- Unique username validation  
- Instant message delivery  
- Persistent log storage (`chat_logs.txt`)  
- Message history for new users  
- Automated system messages  

---

## 🤝 Contributing

Contributions are welcome. Fork the repository, implement improvements, and submit a pull request.

---

## 📄 License

This project is licensed under the **MIT License**. See [LICENSE.md](LICENSE.md) for details.

---

## 🙏 Acknowledgments

Built as part of a Go learning journey with a focus on networking, concurrency, and server-side development.

---

## 👥 Authors

- **Sayed Ahmed Husain** – [sayedahmed97.sad@gmail.com](mailto:sayedahmed97.sad@gmail.com)

---

## 📚 What I Learned

- Building TCP servers in Go  
- Using goroutines and channels effectively  
- Concurrent client handling  
- File-based logging  
- Error handling in multi-user systems  

---

## ⚠️ Limitations

- Maximum of 10 concurrent users  
- No encryption (plain-text communication)  
- Terminal-based interface only  

---

## 🔮 Future Improvements

- Add message encryption  
- Improve terminal UI  
- Develop a dedicated client  
- Support private messaging  
- Enhance scalability  
