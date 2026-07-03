# 🔐 Vault Audit

A security audit tool for your **Bitwarden** vault, inspired by the premium password health report — but **100% local, free, and open source**.

No data ever leaves your browser: no server, no API, no tracking.

![100% local](https://img.shields.io/badge/données-100%25%20locales-3fc98a)
![No dependencies](https://img.shields.io/badge/dépendances-aucune-4f7cff)
![MIT License](https://img.shields.io/badge/licence-MIT-8b90a3)

---

## ✨ Features

- **Global vault score** — a synthetic gauge from 0 to 100 based on weak, duplicated, and reused passwords
- **Duplicate password detection** — automatically groups accounts sharing the exact same password
- **Weak password detection** — real entropy calculation (length × character diversity) + list of overly common passwords
- **Reused username detection** — spots logins/emails used across multiple accounts
- **Password lookup** — paste a password to instantly find all accounts using it
- **Password age** — displays how long it has been since each item was last modified
- **Progress tracking** — check off fixed accounts as you go, with a progress bar saved locally
- **Dark mode interface** inspired by Bitwarden's design

## 🚀 Usage

1. In Bitwarden: **Settings → Export Vault → Export**, in **JSON** format (unencrypted)
2. Open `audit-coffre-fort.html` by double-clicking it (no installation, no server required)
3. Drag and drop the exported JSON file into the designated area, or click to select it
4. Browse the report and fix high-risk accounts

> ⚠️ Once the analysis is complete, remember to delete the exported JSON file: it contains all your passwords in plain text.

## 🔒 Privacy

This project is a **single HTML file**, with no build, no framework, and no external dependencies other than Google Fonts (loaded via CDN, strictly for display purposes).

- No network requests are made with your data
- No cookies, no trackers
- The only persisted data is the list of accounts you have checked as "fixed", stored in your browser's `localStorage` — and never transmitted anywhere

You can verify this yourself: open the source code, there is no `fetch` or `XMLHttpRequest` to any third-party server.

## 🧮 How the score is calculated

The global score (0-100) is a weighted average based on three factors, relative to the total number of accounts:

- **50 %** — proportion of weak or common passwords
- **35 %** — proportion of accounts using a duplicated password
- **15 %** — proportion of accounts using a reused username

A score of 100 means no issues were detected.

## 🛠️ Tech stack

- Vanilla HTML / CSS / JavaScript — no frameworks, no build steps
- Fonts [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk), [Inter](https://fonts.google.com/specimen/Inter) and [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)

## 📋 Known limitations

- The Bitwarden export must be in **unencrypted JSON** format (CSV format is not supported)
- The displayed "age" corresponds to the last modification date of the entry in Bitwarden (`revisionDate`), which might have been updated for reasons other than changing the password itself
- Fix progression is tied to the browser used: it is not synchronized across devices

## 🤝 Contributing

Suggestions and pull requests are welcome. A few ideas for potential improvements:

- Detection of similar passwords (not just identical ones)
- Exporting the report to PDF/CSV
- Filtering by Bitwarden folder
- Marking specific accounts (banks, taxes, etc) as "critical" to prioritize them

## 📄 License

MIT — free to use, modify, and distribute.