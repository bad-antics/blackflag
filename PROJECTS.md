# 🏴 Blackflag Project Suite

A comprehensive collection of Discord bots, desktop applications, and utilities for community management, gaming, and network operations.

---

## 🤖 Discord Bots

| Bot | Description | Repository |
|-----|-------------|------------|
| 🥩 **Beef Bot** | Community engagement bot | [bad-antics/beef-bot](https://github.com/bad-antics/beef-bot) |
| 🚩 **CTF Bot** | Capture The Flag challenges | [bad-antics/ctf-bot](https://github.com/bad-antics/ctf-bot) |
| 🦎 **Lizard Bot** | General utility bot | [bad-antics/lizard-bot](https://github.com/bad-antics/lizard-bot) |
| 👋 **Slap Bot** | Fun interaction bot | [bad-antics/slap-bot](https://github.com/bad-antics/slap-bot) |
| 🎮 **TSGH Bot** | Tournament & gaming bot | [bad-antics/tsgh-bot](https://github.com/bad-antics/tsgh-bot) |
| ⭐ **XP Bot** | Killers XP ranking system | [bad-antics/xp-bot](https://github.com/bad-antics/xp-bot) |

---

## 🖥️ Desktop Applications

| App | Description | Technology | Repository |
|-----|-------------|------------|------------|
| 🖥️ **Bot Monitor** | Discord bot management dashboard | WPF / .NET 8 | [bad-antics/bot-monitor](https://github.com/bad-antics/bot-monitor) |
| 🍍 **Flipper Pineapple Native** | Hardware management tool | WPF / .NET 8 | [bad-antics/flipper-pineapple-native](https://github.com/bad-antics/flipper-pineapple-native) |
| 🐝 **Hive Mind** | Multi-bot orchestration center | WPF / .NET 8 | [bad-antics/hive-mind](https://github.com/bad-antics/hive-mind) |
| 🌐 **Network Sharing Center** | Network management tool | WPF / .NET 8 | [bad-antics/network-sharing-center-native](https://github.com/bad-antics/network-sharing-center-native) |

---

## 🛠️ Tech Stack

### Discord Bots
- **Runtime**: Node.js 20+
- **Framework**: Discord.js v14/v15
- **Database**: SQLite (better-sqlite3)
- **Package Manager**: npm

### Desktop Apps
- **Framework**: .NET 8.0
- **UI**: WPF (Windows Presentation Foundation)
- **Themes**: Custom dark/cyberpunk themes

---

## 🚀 Quick Start

### Running Discord Bots

```bash
cd <bot-folder>
npm install
# Create .env file with DISCORD_TOKEN
npm start
```

### Building Desktop Apps

```bash
cd <app-folder>
dotnet restore
dotnet build
dotnet run
```

---

## 📦 Bot Monitor Features

The Bot Monitor provides centralized control:

- ✅ Real-time bot status monitoring
- ✅ Start/Stop/Restart individual bots
- ✅ Hidden window mode (no PowerShell popups)
- ✅ Full backup & restore functionality
- ✅ Watchdog for auto-restart on crash
- ✅ .env file backup

---

## 🔐 Security

- All `.env` files are gitignored
- Tokens are stored locally only
- Use `.env.example` files for setup templates

---

## 📄 License

MIT License - See individual repositories for details.

---

Made with ❤️ by [bad-antics](https://github.com/bad-antics)
