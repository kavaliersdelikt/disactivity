<p align="center">
  <img src="public/icon.png" alt="Disactivity Logo" width="128" height="128">
</p>

<h1 align="center">Disactivity</h1>

<p align="center">
  <strong>Discord Activity Simulator</strong><br>
  Simulate game activity on Discord by running fake game processes that Discord can detect.
</p>

<p align="center">
  <a href="https://github.com/holasoyender/disactivity/releases/latest">
    <img src="https://img.shields.io/github/v/release/holasoyender/disactivity?style=flat-square" alt="Latest Release">
  </a>
  <a href="https://github.com/holasoyender/disactivity/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/holasoyender/disactivity?style=flat-square" alt="License">
  </a>
</p>

---

## 📖 Description

**Disactivity** is a lightweight desktop application that allows you to simulate playing any game on Discord. Simply select a game from the list, click "Run", and Discord will display that you're playing the selected game - without actually having it installed.

The app fetches the complete list of detectable games directly from Discord's API, so you have access to thousands of games to choose from.

<p align="center">
  <img src="public/banner.png" alt="Disactivity Logo">
</p>

## ✨ Features

- 🎮 **Thousands of Games** - Browse and search through Discord's complete detectable games database
- 🔎 **Flexible Search** - Search matches names, IDs, and aliases without being affected by spaces or punctuation
- ⭐ **Favorites** - Mark your most-used games for quick access
- 🧩 **Executable Fallbacks** - Games without executable data from Discord remain available, with a best-effort process name generated from the game name
- ⏱️ **Live Runtime** - Running games show their actual elapsed time without an artificial time limit
- 🔄 **Auto-Updates** - Built-in updater to keep the app up to date (WIP)
- 🌐 **Multi-language** - Available in English and Spanish

## 📥 Download

Download the latest version from the [GitHub Releases](https://github.com/holasoyender/disactivity/releases/latest) page.


## 🚀 How It Works

1. **Launch Disactivity** - Open the application
2. **Browse Games** - Scroll through the list or use the search bar to find a specific game
3. **Start Playing** - Click the "Run" button on any game card
4. **Discord Detection** - Discord will automatically detect and display the game activity on your profile
5. **Stop Anytime** - Click "Stop" to end the simulated activity

### Technical Details

Disactivity works by:
1. Fetching the list of detectable games from Discord's API
2. Keeping games in the list even when Discord does not provide executable metadata
3. When you select a game, it creates a temporary executable with the same name as the game's actual executable
4. Discord's game detection scans for running processes with known executable names
5. Discord recognizes the process and displays the game activity on your profile
6. When stopped, the temporary files are automatically cleaned up

If Discord does not provide an executable name, Disactivity uses a cleaned-up version of the game name as a fallback. WarDogs is handled explicitly with `WARDOGS.exe`. These fallbacks are best-effort because Discord's actual process name is not available in the API response.

## 🔧 Building from Source

### Prerequisites

- [Node.js](https://nodejs.org/) and npm
- [Rust](https://www.rust-lang.org/tools/install) (latest stable)

### Build Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/holasoyender/disactivity.git
   cd disactivity
   ```

2. **Install dependencies**
   ```bash
    npm install
   ```

3. **Build the slave executable** (required before building the main app)
   ```bash
   cd src-tauri/slave
   cargo build --release
   cd ../..
   ```

4. **Run in development mode**
   ```bash
    npm run tauri dev
   ```

5. **Build for production**
   ```bash
    npm run tauri build
   ```

The built application will be available in `src-tauri/target/release/bundle/`. On Windows, the installer is created in the `nsis` subdirectory.

## 📁 Project Structure

```
disactivity/
├── src/                    # Frontend (React + TypeScript)
│   ├── components/         # UI Components
│   ├── i18n/              # Internationalization
│   │   └── locales/       # Translation files
│   └── lib/               # Utilities
├── src-tauri/             # Backend (Rust + Tauri)
│   ├── src/               # Rust source code
│   ├── slave/             # Slave executable (the fake game process)
│   └── icons/             # Application icons
└── public/                # Static assets
```

## 🛡️ Privacy & Safety

- **No data collection** - Disactivity does not collect or send any personal data
- **Open source** - All code is publicly available for review
- **Local only** - The only network requests are to Discord's public API to fetch the games list

## ⚠️ Disclaimer

This application is for entertainment purposes only. Use responsibly and in accordance with Discord's Terms of Service.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/holasoyender">holasoyender</a>
</p>

