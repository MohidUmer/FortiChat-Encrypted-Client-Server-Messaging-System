# FortiChat – Encrypted Client–Server Messaging System

## 1. Project Overview
Secure communication is essential in modern networked systems. FortiChat is a **terminal-based encrypted messaging system** in **C++**.  
It supports multiple clients connecting to a TCP server and features:

- Encrypted client–server messaging  
- Multi-client support with threads  
- Secure user authentication  
- Admin moderation: ban, kick, restrict  
- Violation tracking & IP-based blocking  
- Streak system & leaderboard  
- Persistent logging of users, bans, and actions  

## 2. Tech Stack

- **Language**: C++  
- **Networking**: Berkeley Sockets (TCP)  
- **Cryptography**: OpenSSL (SHA-256, AES-256, 3DES)  
- **Concurrency**: POSIX Threads  
- **Platform**: Linux / WSL  

## 3. Project Structure

```

FortiChat/
│── src/
│   ├── server.cpp
│   └── client.cpp
│── README.md
│── .gitignore

````

## 4. Setup & Usage

```bash
g++ src/server.cpp -o server -lssl -lcrypto -pthread
./server

g++ src/client.cpp -o client -lssl -lcrypto
./client
```

## 5. Major Components

### 5.1 Server Module (`server.cpp`)

**Responsibilities:**

* Handle multiple clients concurrently
* Authentication & session management
* Admin moderation (ban, kick, restrict)
* Persistent storage for bans and logs

**Admin Commands**

```
users          - List connected users
ban <user>     - Ban a user
unban <user>   - Remove ban
delete <user>  - Delete account
kick <user>    - Disconnect user
restricted     - Show banned users
violations     - Show violations
blocked        - Show blocked IPs
logs           - View logs
broadcast <m>  - Message all users
status         - Server status
help           - Show commands
exit           - Graceful shutdown
```

### 5.2 Client Module (`client.cpp`)

**Responsibilities:**

* Connect to server (`127.0.0.1:8080`)
* Handle secure authentication
* Send/receive encrypted messages
* Respond to server admin actions

**Client Commands**

```
help
broadcast <message>
private <message>
streak
leaderboard
rules
delete
exit
```

## 6. Security & Cryptography

### 6.1 SHA-256 Hashing

* Used for password hashing, identity verification, and data integrity
* **Workflow:** `Password → SHA-256 → Hash → Server Verification`

### 6.2 AES-256 Encryption (Primary)

* Encrypts messages, session tokens, and sensitive commands
* **Modes:** CBC or ECB
* Fast, secure, standard across OS

### 6.3 3DES Encryption (Fallback)

* Used if AES unavailable
* Pros: Simple, legacy compatibility
* Cons: Slower, lower security margin

## 8. Logging & Monitoring

* `admin_logs.txt` – Admin actions
* `violation_logs.txt` – User violations
* `restricted_users.txt` – Persistent bans
* `users.txt` – Credentials and streaks

## 9. Learning Outcomes

* Secure socket programming
* Encryption and hashing techniques
* Multi-threaded network design
* Moderation and logging systems
* Security-aware C++ development

## 10. Limitations

* Terminal-based interface
* No TLS (custom encryption layer)
* File-based storage only
* Session keys stored in memory

## 11. Ethical & Legal Notice

* For **educational and experimental purposes only**
* Controlled environment testing
* Misuse for unauthorized access is prohibited

## 12. Author & Contact

**Name**: Mohid Umer  
**Email**: [mohidumer112@gmail.com](mailto:mohidumer112@gmail.com)  

> FortiChat is a learning project for Linux based network programming and secure encryption solution. Feedback and collaboration are welcome.
