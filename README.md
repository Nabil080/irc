# IRC - Internet Relay Chat Server

**IRC** is a C++ implementation of an Internet Relay Chat (IRC) server, providing multi-user, multi-channel real-time messaging compliant with the RFC 1459 (and some extensions). This project demonstrates network programming, socket management, and protocol parsing, all written from scratch with no external networking libraries.

> **Note**: This server is for educational purposes and may not be secure or production-ready. Explore the code, test with your favorite IRC client, and feel free to experiment.

---

## Features

- **Multi-client support**: Handles multiple simultaneous users via non-blocking sockets.
- **Channels**: Users can create, join, and leave channels.
- **Authentication**: Supports basic nickname and user registration.
- **IRC Commands**: Implements standard IRC commands (`/join`, `/part`, `/nick`, `/privmsg`, `/notice`, `/quit`, etc.).
- **Operator privileges**: Channel ops can kick, ban, and set topics.
- **Private messaging**: Send direct messages to users.
- **Channel modes**: Public/private channels, invite-only, topic locks, etc.
- **Error handling**: Graceful disconnects, unknown commands, and protocol errors.
- **Makefile-driven**: Simple build and run.

---

## Dependencies

- **C++98 or later**
- **make**
- **Linux or macOS** (uses POSIX sockets)
---

## Installation

Clone the repository and build the server:

```sh
git clone https://github.com/Nabil080/irc
cd irc
make
```

---

## Usage

Run the IRC server with default settings:

```sh
./ircserv <port> <password>
```

- `<port>`: Port number to listen on (e.g., `6667`).
- `<password>`: Server password required for clients to connect.

Example:

```sh
./ircserv 6667 mysecret
```

You can now connect with any IRC client (e.g., HexChat, irssi, WeeChat):

- **Server**: `localhost`
- **Port**: `6667`
- **Password**: `mysecret` (if prompted)

---

## Supported Commands

- `/nick <nickname>`: Set/change your nickname
- `/user <username> 0 * :<realname>`: Register with the server
- `/join #channel`: Join or create a channel
- `/part #channel`: Leave a channel
- `/privmsg <nick|#channel> <message>`: Send a message
- `/notice <nick|#channel> <message>`: Send a notice
- `/quit [message]`: Disconnect
- `/topic #channel <topic>`: Set channel topic (op only)
- `/kick #channel <user>`: Kick a user from a channel (op only)
- `/invite <user> #channel`: Invite user to channel (op only)
- `/mode <target> <modes>`: Change user or channel modes

And more! Not all extensions are implemented, see code for full details.

---

## Cleaning Up

To clean build files:

```sh
make clean
```

To remove all binaries and objects:

```sh
make fclean
```

---

## Example Session

```text
$ nc localhost 6667
PASS serversecret
NICK tester
USER tester 0 * :Test User
JOIN #42
PRIVMSG #42 :Hello, IRC!
```

Or connect via a GUI IRC client.
