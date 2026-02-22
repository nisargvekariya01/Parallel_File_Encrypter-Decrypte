# 🔐 AES-256-CTR Parallel Cipher with TUI

A high‑performance, terminal‑based tool for **encrypting** and **decrypting** files using **AES‑256 in CTR mode** with **parallel processing**.  
It features a friendly **ncurses** interface, **HMAC integrity verification**, and automatic file selection – all in one compact utility.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)  
*Built with OpenSSL 3, pthreads, and ncurses.*

---

## ✨ Features

- **AES‑256‑CTR** – strong symmetric encryption with random IV generation.
- **Parallel processing** – splits files into chunks and processes them concurrently (up to 16 threads) for maximum speed.
- **Integrity check** – HMAC‑SHA256 of the plaintext (encryption) or ciphertext (decryption) ensures data has not been tampered with.
- **Terminal UI (TUI)** – easy navigation with arrow keys, file browser, and on‑screen editing.
- **Automatic IV & HMAC storage** – IV and HMAC are saved to separate files (`.iv_data`, `.hmac_data`) for later decryption.
- **Safe path handling** – file browser supports directories and symlinks; output file name is automatically suggested based on the input.
- **Key derivation** – PBKDF2 with 10 000 iterations turns your passphrase into a secure 256‑bit key.

---

## 📋 Prerequisites

Make sure the following development libraries are installed on your system:

- **OpenSSL 3.x** (libssl‑dev / openssl‑devel)
- **ncurses** (libncurses‑dev)
- **pthread** (usually part of glibc)

**Installation examples:**

| Distribution | Command |
|--------------|---------|
| Debian/Ubuntu | `sudo apt install libssl-dev libncurses-dev gcc` |
| Fedora        | `sudo dnf install openssl-devel ncurses-devel gcc` |
| Arch Linux    | `sudo pacman -S openssl ncurses gcc` |

---

## 🔧 Building

Compile the program with a single `gcc` command (no Makefile required):

```bash
gcc -o cipher main.c -lpthread -lssl -lcrypto -lncurses
