# 🔍 Troubleshooting Claude Code

Panduan ringkas mengatasi error umum saat install dan menggunakan Claude Code CLI.

## 📑 Daftar Isi

- Instalasi
- Konfigurasi
- Runtime
- VS Code Extension

---

## 🚫 Instalasi

### npm tidak dikenali
- Penyebab: Node.js belum terinstall atau PATH belum diset.
- Solusi:
  1. Install Node.js LTS, pilih "Add to PATH"
  2. Restart terminal
  3. Verifikasi `node --version` dan `npm --version`
  4. Install Claude Code: `npm install -g @anthropic-ai/claude-code`

### npm.ps1 cannot be loaded
- Penyebab: PowerShell execution policy membatasi script
- Solusi:
  - Jalankan PowerShell sebagai Administrator:  
    `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`
  - Atau gunakan CMD

### Network/Connection Error (ENOTFOUND)
- Penyebab: DNS/proxy/firewall
- Solusi: ganti DNS, cek proxy, atau pakai mirror:  
  `npm install -g @anthropic-ai/claude-code --registry https://registry.npmmirror.com`

### Permission Denied
- Windows: Jalankan sebagai Administrator  
- Mac/Linux: Gunakan `sudo`

---

## ⚙️ Konfigurasi

### API key tidak bekerja
- Pastikan environment variables:
  - Windows: `$env:ANTHROPIC_AUTH_TOKEN`
  - Mac/Linux: `$ANTHROPIC_AUTH_TOKEN`
- Alternatif: buat `~/.claude/settings.json` dengan API key dan base URL

### Dialihkan ke Anthropic Console
- Penyebab: Claude Code default login ke Anthropic
- Solusi: gunakan `settings.json` atau environment variables langsung

---

## 🚀 Runtime

### Claude Code butuh Git Bash (Windows)
- Pastikan Git Bash terinstall dan ada di PATH  
- Atau set variable: `CLAUDE_CODE_GIT_BASH_PATH`

### Claude Code tidak bisa akses file
- Jalankan di folder project  
- Pastikan folder permission sesuai

### claude: command not found
- Solusi:
  1. Cek install: `npm list -g @anthropic-ai/claude-code`
  2. Jika belum, install
  3. Restart terminal
  4. Pastikan npm global bin ada di PATH

### Rate Limit Exceeded / Context Window Limit
- Tunggu beberapa detik, mulai percakapan baru, atau gunakan `/compact`

### Auto-update failed
- Gunakan `claude doctor` untuk diagnosa  
- Atau install ulang via npm

### 401 Invalid bearer token
- Pastikan API key valid di environment variables atau settings.json

---

## 🖥️ VS Code Extension

### Setup Claude Code Extension
- Install dari Marketplace  
- Pastikan path Claude Code CLI sesuai environment
