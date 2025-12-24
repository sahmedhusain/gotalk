# GoTalk 💬🚀

[![Go](https://img.shields.io/badge/Go-1.20+-00ADD8?style=flat&logo=go)](https://golang.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE.md)

GoTalk is a simple TCP-based chat server written in Go. It lets multiple users chat in real-time from their terminals. Key features include sending messages to everyone, unique usernames, timestamps on messages, and keeping a log of the chat. It's great for quick chats or team discussions.

## Features ✨

- **Real-time Messaging** 💬: Messages are sent instantly to all connected users.
- **Unique Usernames** 👤: Each person must choose a name that no one else is using.
- **Timestamps** ⏰: Every message shows the exact time it was sent.
- **Chat Logs** 📝: All messages and events are saved to a file for later review.
- **Multiple Connections** 🔄: The server can handle up to 10 users at the same time using Go's goroutines.
- **Join/Leave Alerts** 🚪: Users are notified when someone enters or exits the chat.
- **Message History** 📜: New users see recent messages when they join.

## Technologies Used 🛠️

The project uses:

- **Go** 🐹: The main programming language for building the server, handling connections, and managing tasks at the same time.
- **TCP/IP** 🌐: The network protocol that ensures reliable communication between the server and clients.
- **Goroutines** ⚡: Go's way of running multiple tasks concurrently without slowing down.
- **Channels** 📡: Tools in Go for safe communication between different parts of the program.
- **File I/O** 💾: Basic file operations to save and read chat logs.

## What We Aim For 🎯

GoTalk creates a basic chat experience over TCP connections. The server handles:

1. **Users**: Connections with unique names to avoid mix-ups.
2. **Messages**: Broadcasting them in real-time and saving them with timestamps.
3. **Events**: Notifications for when users join or leave, processed in the background.
4. **History**: Sending recent messages to new users so they can catch up.

We use simple data structures and Go's concurrency features to keep things running smoothly.

## Getting Started 🚀

### Prerequisites

- Go version 1.20 or newer on your computer.
- A terminal (command prompt) to run commands and connect as a client.

### Installation

1. Download the code:
   ```bash
   git clone https://github.com/sahmedhusain/gotalk.git
   ```
2. Go into the project folder:
   ```bash
   cd gotalk
   ```
3. Install any needed packages:
   ```bash
   go mod tidy
   ```
4. Start the server:
   ```bash
   go run main.go
   ```

## How to Use 📖

Run the server first. Then, use a tool like NetCat to connect as a client. Type a unique name and start chatting. The server listens on localhost port 8989 by default.

### Example Connection

- Connect as a client:
  ```bash
  nc localhost 8989
  ```
- You'll see:
  ```
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
  (Enter a name, e.g., Alice)

## Terminal Examples 💻

### Starting the Server

```bash
$ go run main.go
Server is running on Port :8989
```

### Chatting Between Users

```bash
$ nc localhost 8989
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
[ENTER YOUR NAME]: Alice
[2024-10-12 15:12:45][system]: Alice joined the chat

$ nc localhost 8989
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
[ENTER YOUR NAME]: Bob
[2024-10-12 15:13:00][system]: Bob joined the chat
[2024-10-12 15:13:02][Alice]: Hi Bob!
[2024-10-12 15:13:05][Bob]: Hello Alice!
[2024-10-12 15:13:10][Alice]: How is everyone doing today?
[2024-10-12 15:13:15][Bob]: Great, thanks! Excited to chat.
```

### When Someone Leaves

```bash
[2024-10-12 15:14:00][system]: Bob has left our chat...
```

## Under the Hood 🔧

### How Data is Handled

The server uses Go's network tools to manage connections. Each user gets their own goroutine to read and write messages. A central channel broadcasts messages to everyone.

### Server Side

- **Connections**: Each client spawns a goroutine for handling input and output.
- **Broadcasting**: A main goroutine sends messages to all users.
- **Logging**: Events are written to a file with times and user info.
- **Concurrency**: Locks prevent issues when multiple users act at once.
- **Errors**: The server handles disconnections and bad inputs gracefully.

### Networking

- **TCP Sockets**: Ensure messages arrive reliably.
- **Broadcasting**: Uses channels for efficient message sharing.
- **Limits**: Currently up to 10 users to keep it simple.

The design makes it easy to add features later.

## Chat Details 📋

The system includes:

- **Unique Names**: The server checks for duplicates and asks for a different name if needed.
- **Instant Updates**: Messages show up right away for all users.
- **Saved Logs**: Everything goes to `chat_logs.txt` in an easy-to-read format.
- **History for New Users**: They get the last few messages automatically.
- **System Messages**: Automatic notes for joins, leaves, and issues.

## Contributing 🤝

We welcome contributions. Fork the repo, make your changes, and submit a pull request. Follow Go's style guidelines and test your code.

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/NewFeature`).
3. Make your changes and commit them (`git commit -m 'Add NewFeature'`).
4. Push to your branch (`git push origin feature/NewFeature`).
5. Open a pull request.

## License 📄

This project uses the MIT License. See LICENSE.md for details.

## Acknowledgments 🙏

This was built while learning Go, with a focus on networking and running things in parallel. Thanks to the Go community for their help.

## Authors 👥

- **Sayed Ahmed Husain** - [sayedahmed97.sad@gmail.com](mailto:sayedahmed97.sad@gmail.com)

## What I Learned 📚

Working on GoTalk taught me:

- How to build a TCP server in Go.
- Using goroutines and channels for concurrent tasks.
- Basics of network programming with sockets.
- Saving data to files for logs.
- Handling errors in a multi-user system.
- Organizing Go code in a clean way.

## Limitations ⚠️

- **User Limit**: Only 10 users at once. You can change this in the code.
- **No Security**: Messages are plain text. Add encryption for real use.
- **Terminal Only**: Needs command-line tools; no graphical interface.

## Future Improvements 🚀

- Add encryption for secure chats.
- Create a better interface for the terminal.
- Build a dedicated client app.
- Include user login and private messages.
- Make it handle more users with better scaling.
