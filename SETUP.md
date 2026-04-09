````markdown
# CARA INSTALL CLAUDE CODE (WINDOWS, MAC/LINUX)  
_Melalui VS Code Extension dan CLI_

---

## Apa itu Claude Code
**Claude Code** adalah tool dari **Anthropic** untuk chat dengan Claude AI. Ada dua cara pakai:

**Fungsi utama:**
- Chat dengan Claude AI
- Code review & debugging
- Diskusi project
- Context-aware terhadap file project

---

## Syarat Awal
- **Node.js 18+** → [nodejs.org](https://nodejs.org)  
- **API Key** dari seller  
- **Terminal** (CMD / PowerShell / Bash) atau **VS Code**  
- **Koneksi Internet**

---

## Install Claude Code

### Windows
```bash
npm install -g @anthropic-ai/claude-code
````

**Jika muncul permission error:**
Buka **PowerShell sebagai Administrator**

**Jika belum ada Git:**
Download [Git for Windows](https://git-scm.com/download/win)

### Mac / Linux

```bash
npm install -g @anthropic-ai/claude-code
```

**Jika muncul permission error:**
Tambahkan `sudo` sebelum perintah

---

## 🔑 Setup API Key

### A. Via Environment Variables (Direkomendasikan)

**Windows (PowerShell/CMD)**

```powershell
setx ANTHROPIC_AUTH_TOKEN "YOUR_API_KEY"
setx ANTHROPIC_BASE_URL "https://api.minimax.io/anthropic"
```

*Tutup terminal & buka lagi agar environment variables aktif*

**Mac/Linux**

```bash
export ANTHROPIC_AUTH_TOKEN="YOUR_API_KEY"
export ANTHROPIC_BASE_URL="https://api.minimax.io/anthropic"
```

**Permanen (opsional, Mac/Linux)**

```bash
echo 'export ANTHROPIC_AUTH_TOKEN="YOUR_API_KEY"' >> ~/.bash_profile
echo 'export ANTHROPIC_BASE_URL="https://api.minimax.io/anthropic"' >> ~/.bash_profile
source ~/.bash_profile
```

### B. Via `settings.json` (Optional)

**Windows**

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude"

@"
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "YOUR_API_KEY",
    "ANTHROPIC_BASE_URL": "https://api.minimax.io/anthropic",
    "API_TIMEOUT_MS": "3000000"
  }
}
"@ | Out-File -FilePath "$env:USERPROFILE\.claude\settings.json" -Encoding utf8
```

**Mac / Linux**

```bash
mkdir -p ~/.claude
cat > ~/.claude/settings.json << 'EOF'
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "YOUR_API_KEY",
    "ANTHROPIC_BASE_URL": "https://api.minimax.io/anthropic",
    "API_TIMEOUT_MS": "3000000"
  }
}
EOF
```

---

## ✅ Verifikasi Setup

```bash
node --version
claude --version
echo $ANTHROPIC_AUTH_TOKEN       # Mac/Linux
echo %ANTHROPIC_AUTH_TOKEN%      # Windows
```

*Jalankan `claude` di terminal dan pastikan muncul interface chat*

---

## Cara Menggunakan

### CLI (Terminal)

```bash
cd /path/to/project
claude
```

**Command utama:**

* `/status` – cek model & config
* `/cost` – lihat token usage
* `/model` – ganti model
* `/exit` – keluar

### VS Code Extension

1. Install **Claude Code Extension** di VS Code
2. Klik ikon **Claude** di sidebar → muncul panel chat
3. Bisa pakai **environment variables** atau **settings.json**
4. Tidak perlu run `claude` di terminal saat pakai panel

---

## ⚠️ Troubleshooting Singkat

* `npm not found` → install Node.js, restart terminal
* `claude: command not found` → `npm install -g @anthropic-ai/claude-code`, restart terminal
* Invalid API Key → cek typo, restart terminal, periksa `settings.json`
* VS Code Extension tidak muncul → restart VS Code sepenuhnya

> Untuk troubleshooting lengkap, buat file terpisah `troubleshooting.md`

---

## 🔒 Keamanan

* Jangan share API Key
* Jangan commit API Key ke Git (`.gitignore`)
* Jangan screenshot terminal dengan API Key
* Jika key ter-leak → hubungi seller untuk **revoke**

---

## Uninstall

```bash
npm uninstall -g @anthropic-ai/claude-code
```

**Mac/Linux:** `rm -rf ~/.claude`
**Windows:** `Remove-Item $env:USERPROFILE\.claude -Recurse`

```