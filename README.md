# EvoChess

![EvoChess Logo]

EvoChess is a polished Android chess app built in Kotlin using modern Android Jetpack libraries.  
It focuses on single-player play against a built-in engine, daily puzzles, player profiles, and light gamification. The app is designed to be responsive, work offline-first, and provide a clean, modern chess experience on Android devices.

---

# Key Features

- **Play vs AI**
  - Play full games against a bundled chess engine (e.g., Stockfish).
  - Multiple difficulty levels and engine thinking-time settings.
  - Move validation, legal-move highlighting, undo/redo and hints.

- **Daily Puzzles & Puzzle Library**
  - Fetch and cache a daily puzzle.
  - Browse and solve a local library of cached puzzles.
  - Immediate move feedback with success/failure handling.

- **Game Save & Review**
  - Save games in PGN/FEN format.
  - View game history and replay past games move-by-move.
  - Export and import PGN files.

- **Player Profiles & Progression**
  - Local user profiles with XP, levels and achievements (badges).
  - Track statistics (games played, wins/losses, puzzles solved).

- **Themes & UI Customization**
  - Multiple board and piece themes.
  - Light/dark theme support and basic UI customization.

- **Offline-first with Sync**
  - Primary data stored locally with Room (SQLite).
  - Background tasks (WorkManager) fetch puzzles and sync queued items when online.

- **Notifications**
  - Push notifications for new daily puzzles and achievements (FCM or equivalent).

- **Localization**
  - English and Afrikaans (runtime switching supported).

- **Security Basics**
  - Local accounts with hashed passwords and optional cloud backup.

---

# Screens / User Flows

- **Login / Register** — Create or access a local profile (passwords hashed).
- **Home / Dashboard** — Quick access to Play, Daily Puzzle, and recent games.
- **Game Board** — Interactive 8×8 board, move input by tapping or dragging, engine moves shown instantly.
- **Puzzles** — Solve the daily puzzle or browse the puzzle library.
- **Game History / Review** — List of saved games with replay and export options.
- **Profile / Achievements** — View XP, levels, badges and stats.
- **Settings** — Theme, language toggle, sync preferences, clear local data.

---

# Technology / Libraries (High Level)

- Kotlin, Android Jetpack (ViewModel, LiveData/Flow, Room)
- Kotlin Coroutines for background concurrency
- Room for local persistence (User, Game, Puzzle, Achievement, Settings)
- WorkManager for scheduled/background tasks (puzzle fetch & sync)
- Retrofit / OkHttp for remote API calls (puzzles / optional backup)
- Bundled chess engine (Stockfish or similar) via native library or integrated module
- Firebase (optional): Auth (SSO), Cloud Messaging (notifications), Firestore / Storage for backups

---

# Installation & Running (Developer)

1. Clone the repository:
```bash
git clone <repo-url>
cd evoc h ess
```

2. Open the project in **Android Studio** and let Gradle sync.

3. Connect an Android device (USB debugging) or start an emulator.

4. Run the app from Android Studio or use Gradle:
```bash
./gradlew installDebug
```

**Build commands**
```bash
# Debug APK
./gradlew assembleDebug

# Release AAB (configure signingConfigs in app/build.gradle)
./gradlew bundleRelease
```

---

# Configuration Notes

- **Engine:** If using a native engine (Stockfish), ensure the NDK and native binaries are present in `native/` or `stockfish/`.
- **Remote features:** Daily puzzles, cloud backup and notifications require API keys / Firebase configuration. Add those values to local config files as described in project docs.
- **Language:** To add/update translations edit `res/values/strings.xml` and `res/values-af/strings.xml`.

---

# Data & Backups

- Important app data (games, puzzles, settings) is persisted locally in Room.
- Optional cloud backup stores PGNs and user profile snapshots in a NoSQL store (e.g., Firestore) and media/screenshots in blob storage (e.g., Firebase Storage or S3) when the user enables sync.

---

# Testing & Quality

- Unit tests cover core logic (move validation, FEN/PGN parsing, ViewModel behavior).
- Instrumented tests cover login and primary UI flows (when configured).
- An example CI workflow is included to run tests and build on push/PR.

---

# Troubleshooting

- **App fails to start / engine missing:** Ensure native engine binaries are present or use the fallback pure-Kotlin engine.
- **Puzzle fetch fails:** Check network connectivity and API key configuration.
- **Notifications not received:** Verify Firebase configuration and that device notifications are enabled.

---

# Contributing

1. Fork the repo and create a feature branch.
2. Add tests for new behavior.
3. Open a pull request with a clear description of changes.

---

# License & Credits

- License: MIT (add `LICENSE` file in repo root).
- Credits: Be sure to credit any UI assets, engine code or third-party libraries in `ACKNOWLEDGEMENTS.md`.

---

# Quick Preview

![Play](assets/board.png) ![Stats](assets/trophy.png)

---

Thank you for using EvoChess — if you'd like the README adjusted, different icons, or a README placed directly into your project ZIP, tell me and I'll update it.
