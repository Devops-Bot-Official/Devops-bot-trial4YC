# 🚀 DevOps Bot CLI Installer

This repository contains pre-built installers and binaries for the **DevOps Bot CLI tool**, packaged for major operating systems.

---

## 📦 Releases

| Platform  | File Name                    | Format   |
|-----------|------------------------------|----------|
| Linux     | `devops-bot_0.1_amd64.deb`   | Debian-based `.deb` |
| Linux     | `devops-bot-0.1-1.x86_64.rpm`| RHEL-based `.rpm`   |
| Windows   | `dob.exe`                    | Standalone EXE      |
| macOS     | `dob-macos`                  | Standalone binary   |

---

## 🛠️ Installation Instructions

### 🐧 Linux (Debian/Ubuntu)

```bash
sudo dpkg -i devops-bot_0.1_amd64.deb
```

### 🐧 Linux (RHEL/CentOS/Fedora)

```bash
sudo rpm -i devops-bot-0.1-1.x86_64.rpm
```

### 🍎 macOS

```bash
chmod +x dob-macos
sudo mv dob-macos /usr/local/bin/dob
dob --help
```

### 🪟 Windows

Just double-click `dob.exe` or run from terminal:

```powershell
dob.exe --help
```

---

## 👤 Author

**root**

---

## 🏷️ Release

**First Release:** `test2`  
**Commit Hash:** `25ce770`

---

For any issues or feedback, please open an issue or contact `info@devops-bot.com`.
