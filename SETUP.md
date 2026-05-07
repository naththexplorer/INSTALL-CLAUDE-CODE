# Cara Install Claude Code

Panduan ini menjelaskan cara install dan setup Claude Code API Access untuk Windows, Mac, dan Linux.

Claude Code dapat digunakan melalui:

- CLI/Terminal
- VS Code

## Syarat Awal

Pastikan sudah memiliki:

- Node.js 18+
- API Key dari seller/admin
- Koneksi internet
- Terminal atau VS Code
- Git for Windows khusus pengguna Windows

Cek Node.js:

```bash
node --version
```

Jika belum ada Node.js, install dari:

```text
https://nodejs.org
```

Untuk Windows, disarankan install Git for Windows:

```text
https://git-scm.com/downloads/win
```

---

## Install Claude Code

Jalankan command berikut:

```bash
npm install -g @anthropic-ai/claude-code
```

Cek instalasi:

```bash
claude --version
```

Jika command `claude` belum terbaca, restart terminal atau komputer.

---

## Setup API Key

Ada dua cara setup:

- Environment Variables
- settings.json

Pilih salah satu.

---

## Opsi A - Environment Variables

### Windows PowerShell

```powershell
setx ANTHROPIC_AUTH_TOKEN "YOUR_API_KEY"
setx ANTHROPIC_BASE_URL "https://ai.bluepack.my.id/anthropic"
```

Setelah menjalankan command, tutup terminal lalu buka kembali.

Cek hasilnya:

```powershell
echo $env:ANTHROPIC_AUTH_TOKEN
echo $env:ANTHROPIC_BASE_URL
```

### Windows CMD

Cek hasilnya:

```cmd
echo %ANTHROPIC_AUTH_TOKEN%
echo %ANTHROPIC_BASE_URL%
```

### Mac/Linux

```bash
export ANTHROPIC_AUTH_TOKEN="YOUR_API_KEY"
export ANTHROPIC_BASE_URL="https://ai.bluepack.my.id/anthropic"
```

Agar permanen, tambahkan ke shell config.

Untuk Bash:

```bash
echo 'export ANTHROPIC_AUTH_TOKEN="YOUR_API_KEY"' >> ~/.bashrc
echo 'export ANTHROPIC_BASE_URL="https://ai.bluepack.my.id/anthropic"' >> ~/.bashrc
source ~/.bashrc
```

Untuk Zsh:

```bash
echo 'export ANTHROPIC_AUTH_TOKEN="YOUR_API_KEY"' >> ~/.zshrc
echo 'export ANTHROPIC_BASE_URL="https://ai.bluepack.my.id/anthropic"' >> ~/.zshrc
source ~/.zshrc
```

Cek hasilnya:

```bash
echo $ANTHROPIC_AUTH_TOKEN
echo $ANTHROPIC_BASE_URL
```

---

## Opsi B - settings.json

### Windows PowerShell

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude"

@"
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "YOUR_API_KEY",
    "ANTHROPIC_BASE_URL": "https://ai.bluepack.my.id/anthropic",
    "API_TIMEOUT_MS": "3000000"
  }
}
"@ | Out-File -FilePath "$env:USERPROFILE\.claude\settings.json" -Encoding utf8
```

### Mac/Linux

```bash
mkdir -p ~/.claude

cat > ~/.claude/settings.json << 'EOF'
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "YOUR_API_KEY",
    "ANTHROPIC_BASE_URL": "https://ai.bluepack.my.id/anthropic",
    "API_TIMEOUT_MS": "3000000"
  }
}
EOF
```

Ganti `YOUR_API_KEY` dengan API Key yang diberikan oleh seller/admin.

---

## Verifikasi Setup

Cek Node.js:

```bash
node --version
```

Cek Claude Code:

```bash
claude --version
```

Cek API Key di Mac/Linux:

```bash
echo $ANTHROPIC_AUTH_TOKEN
```

Cek API Key di Windows CMD:

```cmd
echo %ANTHROPIC_AUTH_TOKEN%
```

Cek API Key di Windows PowerShell:

```powershell
echo $env:ANTHROPIC_AUTH_TOKEN
```

---

## Cara Menggunakan CLI

Masuk ke folder project:

```bash
cd path/to/project
```

Jalankan Claude Code:

```bash
claude
```

Command yang sering digunakan:

```text
/status  - cek status konfigurasi
/cost    - lihat token usage
/model   - cek atau ganti model jika tersedia
/exit    - keluar
```

---

## Cara Menggunakan VS Code

1. Buka VS Code
2. Buka folder project
3. Pastikan Claude Code sudah terinstall
4. Buka Claude Code dari extension/sidebar jika tersedia
5. Gunakan API Key yang sudah diset melalui environment variables atau settings.json

---

## Cek Limit

Cek usage dan sisa limit melalui:

```text
https://ai.bluepack.my.id/usage
```

Masukkan data yang diminta pada halaman tersebut untuk melihat status pemakaian.

Limit paket:

```text
220 request / 5 jam
2.200 request / minggu
```

---

## Troubleshooting

### `claude` tidak terbaca

Coba:

```bash
claude --version
```

Jika tetap tidak terbaca:

- Restart terminal
- Restart komputer
- Pastikan Node.js dan npm sudah terinstall
- Pastikan global npm path sudah masuk PATH

### `npm not found`

Install Node.js dari:

```text
https://nodejs.org
```

Lalu restart terminal.

### API Key tidak terbaca

Pastikan API Key sudah benar.

Jika menggunakan environment variables, tutup terminal lalu buka lagi.

Jika menggunakan `settings.json`, pastikan file berada di lokasi:

Windows:

```text
C:\Users\NAMA_USER\.claude\settings.json
```

Mac/Linux:

```text
~/.claude/settings.json
```

### Limit habis

Cek usage:

```text
https://ai.bluepack.my.id/usage
```

Jika limit habis, tunggu kuota tersedia kembali mengikuti sistem rolling window.

---

## Keamanan

Jangan share API Key ke orang lain.

Jangan commit API Key ke GitHub.

Jangan screenshot terminal yang menampilkan API Key.

Jika API Key bocor, segera hubungi seller/admin.

---

## Uninstall

```bash
npm uninstall -g @anthropic-ai/claude-code
```

Hapus konfigurasi Claude Code.

Mac/Linux:

```bash
rm -rf ~/.claude
```

Windows PowerShell:

```powershell
Remove-Item $env:USERPROFILE\.claude -Recurse
```