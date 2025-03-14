# irc - Custom IRC Server

## About

**ft_irc** is a lightweight IRC server built from scratch in **C++98**. It allows multiple clients to connect, chat in channels, and interact using standard IRC commands. The project focuses on efficient, non-blocking I/O operations and a simple yet functional feature set. This server was built with **IRSSI** as the reference client.

This project was made in collaboration with [@corentin-ltc](https://github.com/corentin-ltc/) and [@DavidLi760](https://github.com/DavidLi760)

## Features

- **Multi-client support** via a single poll loop
- **User authentication** with a connection password
- **Channel management** with operator and user roles
- **Implemented IRC commands**:
  - `INFO` → Display server information
  - `ADMIN` → Display admin information
  - `PASS <password>` → Authenticate with the server password
  - `PING <token>` → Keep connection alive
  - **User authentication & session management**:
    - `NICK <nickname>` → Set or change nickname
    - `USER <username> <hostname> <servername> <realname>` → Set user details
  - **Channel operations**:
    - `JOIN #channel1,#channel2,...` → Join one or multiple channels
    - `PART #channel [message]` → Leave a channel with an optional message
    - `PRIVMSG <user/channel> <message>` → Send a private or channel message
    - `OPER <username> <password>` → Gain operator privileges
  - **Operator commands**:
    - `KICK <channel> <user>` → Remove a user from a channel
    - `INVITE <user> <channel>` → Invite a user to a channel
    - `TOPIC <channel> <topic>` → Set or view channel topic
    - `MODE <channel> <modes>` → Manage channel settings (`invite-only`, `password`, etc.)

## Dependencies

- A C++98-compliant compiler
- `make` (for building the project)

## Installation

Clone the repository and build the project:

```sh
git clone https://github.com/Nabil080/irc
cd irc
make
```

## Usage

Run the server with a specified port and password:

```sh
./ircserv <port> <password>
```

Example:
```sh
./ircserv 6667 mypassword
```

## Connecting to the Server

Use an IRC client like IRSSI to connect:

```sh
irssi
/connect 127.0.0.1 6667 mypassword
```

For more extreme testing, you can connect directly using `nc` (Netcat), but you must use the correct raw command format (e.g., `JOIN #channel` instead of `/join #channel`):

```sh
nc -C 127.0.0.1 6667
```
Then manually enter commands like:
```
PASS mypassword
NICK testuser
USER testuser 0 * :Real Name
JOIN #testchannel
```

## Cleaning Up

To remove compiled files, run:

```sh
make clean
```

To completely remove all binaries and object files:

```sh
make fclean
```

