# 🧠 Mini Redis Clone (Vanilla JavaScript)

A **lightweight Redis-like in-memory datastore** built from scratch using **Node.js TCP sockets** and **vanilla JavaScript**.  
This project implements a subset of Redis commands, supports the **RESP protocol**, **key expiration**, **lists**, and **persistence (AOF & snapshot)**.

> ⚠️ Educational project inspired by Redis internals. Not intended for production use.

---

## ✨ Features

- 📡 TCP server compatible with Redis clients
- 🧩 RESP protocol implementation
- 🗄️ In-memory key-value store
- ⏱️ Key expiration with TTL support
- 📜 Append Only File (AOF) persistence
- 💾 Snapshot (RDB-like) persistence
- 📚 List data structure support
- 🔢 Atomic counters (INCR / DECR)
- 🧪 Full integration test coverage
- 🪵 Namespace-based debug logger

---

## 📁 Project Structure

mini-redis-clone
│
├── src
│ ├── utils
│ │ ├── index.js # RESP command builder
│ │ └── logger.js # Debug logger
│ │
│ ├── config.json # Persistence configuration
│ ├── core.js # Command handlers & execution
│ ├── persistence.js # Snapshot & AOF logic
│ └── server.js # TCP server (port 6379)
│
└── test
└── server.test.js # Integration tests


---

## ⚙️ Supported Commands

### 🔑 String Commands
- `SET key value`
- `GET key`
- `DEL key`
- `INCR key`
- `DECR key`

### ⏳ Expiration Commands
- `EXPIRE key seconds`
- `TTL key`

### 📚 List Commands
- `LPUSH key value [value ...]`
- `RPUSH key value [value ...]`
- `LPOP key`
- `RPOP key`
- `LRANGE key start stop`

### ⚠️ Other
- `COMMAND`
- Graceful handling of unknown commands

---

## 💾 Persistence

Configured via `src/config.json`:

```json
{
  "snapshot": false,
  "snapshotInterval": 5000,
  "appendonly": true,
  "aofCommands": [
    "SET",
    "DEL",
    "EXPIRE",
    "INCR",
    "DECR",
    "LPUSH",
    "RPUSH",
    "LPOP",
    "RPOP"
  ]
}
