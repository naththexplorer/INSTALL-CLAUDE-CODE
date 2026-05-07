# Troubleshooting Claude Code

Panduan ringkas mengatasi error umum saat install dan menggunakan Claude Code CLI.

## Daftar Isi

- Instalasi
- Konfigurasi
- Runtime
- VS Code Extension
- Limit dan Usage
- Keamanan

---

## Instalasi

### `npm` tidak dikenali

Penyebab:

- Node.js belum terinstall
- PATH belum terset
- Terminal belum direstart setelah install Node.js

Solusi:

1. Install Node.js LTS dari:

```text
https://nodejs.org
```

2. Saat install, pastikan opsi `Add to PATH` aktif.
3. Restart terminal.
4. Verifikasi:

```bash
node --version
npm --version
```

5. Install Claude Code:

```bash
npm install -g @anthropic-ai/claude-code
```

---

### `npm.ps1 cannot be loaded`

Penyebab:

PowerShell execution policy membatasi script.

Solusi 1 — ubah execution policy:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Tutup PowerShell, lalu buka kembali.

Solusi 2 — gunakan CMD:

```cmd
npm install -g @anthropic-ai/claude-code
```

---

### Network / Connection Error `ENOTFOUND`

Penyebab umum:

- DNS bermasalah
- Proxy/firewall memblokir koneksi
- Koneksi internet tidak stabil
- Registry npm sedang lambat

Solusi:

1. Cek koneksi internet.
2. Ganti DNS jika perlu.
3. Matikan VPN/proxy sementara jika mengganggu.
4. Coba install lewat mirror:

```bash
npm install -g @anthropic-ai/claude-code --registry https://registry.npmmirror.com
```

---

### Permission Denied

#### Windows

Jalankan terminal sebagai Administrator, lalu ulangi install:

```bash
npm install -g @anthropic-ai/claude-code
```

#### Mac/Linux

Gunakan `sudo` jika diperlukan:

```bash
sudo npm install -g @anthropic-ai/claude-code
```

Jika tetap bermasalah, cek permission folder global npm.

---

## Konfigurasi

### API key tidak bekerja

Pastikan API Key sudah benar dan tidak terpotong.

Cek environment variables.

#### Windows PowerShell

```powershell
echo $env:ANTHROPIC_AUTH_TOKEN
echo $env:ANTHROPIC_BASE_URL
```

#### Windows CMD

```cmd
echo %ANTHROPIC_AUTH_TOKEN%
echo %ANTHROPIC_BASE_URL%
```

#### Mac/Linux

```bash
echo $ANTHROPIC_AUTH_TOKEN
echo $ANTHROPIC_BASE_URL
```

Pastikan base URL:

```text
https://ai.bluepack.my.id/anthropic
```

Jika environment variables tidak terbaca, gunakan `settings.json`.

---

### Setup ulang API key via `settings.json`

#### Windows PowerShell

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

#### Mac/Linux

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

Ganti `YOUR_API_KEY` dengan API Key dari seller/admin.

---

### Dialihkan ke Anthropic Console

Penyebab:

Claude Code default bisa mencoba login ke Anthropic jika API key/base URL belum terbaca.

Solusi:

1. Pastikan `ANTHROPIC_AUTH_TOKEN` sudah diset.
2. Pastikan `ANTHROPIC_BASE_URL` sudah diset ke:

```text
https://ai.bluepack.my.id/anthropic
```

3. Gunakan `settings.json` jika environment variables tidak terbaca.
4. Restart terminal.
5. Jalankan ulang:

```bash
claude
```

---

### `401 Invalid bearer token`

Penyebab:

- API Key salah
- API Key terpotong
- API Key sudah tidak aktif
- API Key tidak terbaca oleh Claude Code

Solusi:

1. Pastikan API Key sama persis dengan yang diberikan seller/admin.
2. Jangan tambahkan spasi, tanda kutip ekstra, atau karakter lain.
3. Cek environment variables atau `settings.json`.
4. Jika masih error, hubungi seller/admin untuk pengecekan API Key.

---

## Runtime

### Claude Code butuh Git Bash di Windows

Penyebab:

Claude Code kadang membutuhkan Git Bash untuk menjalankan perintah shell di Windows.

Solusi:

1. Install Git for Windows:

```text
https://git-scm.com/downloads/win
```

2. Pastikan Git Bash masuk PATH.
3. Restart terminal atau komputer.

Jika perlu, set path Git Bash:

```powershell
setx CLAUDE_CODE_GIT_BASH_PATH "C:\Program Files\Git\bin\bash.exe"
```

---

### Claude Code tidak bisa akses file project

Penyebab:

- Claude Code dijalankan di folder yang salah
- Permission folder bermasalah
- Project belum dibuka dari root folder

Solusi:

1. Masuk ke folder project:

```bash
cd path/to/project
```

2. Jalankan Claude Code dari folder tersebut:

```bash
claude
```

3. Pastikan file project memang ada di folder itu.
4. Jika memakai VS Code, buka folder project, bukan hanya satu file.

---

### `claude: command not found`

Penyebab:

- Claude Code belum terinstall
- npm global bin belum masuk PATH
- Terminal belum direstart

Solusi:

1. Cek apakah Claude Code terinstall:

```bash
npm list -g @anthropic-ai/claude-code
```

2. Jika belum, install:

```bash
npm install -g @anthropic-ai/claude-code
```

3. Restart terminal.
4. Cek versi:

```bash
claude --version
```

Jika masih tidak terbaca, cek npm global bin:

```bash
npm bin -g
```

Pastikan path tersebut masuk ke PATH sistem.

---

### Rate Limit Exceeded

Penyebab:

Limit request 5 jam atau weekly limit sedang habis.

Limit paket:

```text
220 request / 5 jam
2.200 request / minggu
```

Solusi:

1. Cek sisa limit:

```text
https://ai.bluepack.my.id/usage
```

2. Tunggu kuota tersedia kembali.
3. Hindari menjalankan banyak agent bersamaan.
4. Gunakan prompt lebih ringkas dan jelas.
5. Jika masih bermasalah, hubungi seller/admin.

---

### Context Window Limit

Penyebab:

Percakapan terlalu panjang atau terlalu banyak file/context yang dimasukkan.

Solusi:

1. Gunakan command:

```text
/compact
```

2. Mulai percakapan baru.
3. Minta AI fokus hanya pada file yang relevan.
4. Hindari memasukkan terlalu banyak file sekaligus.
5. Pecah task besar menjadi beberapa task kecil.

---

### Auto-update failed

Solusi:

1. Jalankan diagnosa:

```bash
claude doctor
```

2. Jika masih gagal, install ulang:

```bash
npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code
```

---

### Claude Code lambat atau stuck

Penyebab umum:

- Task terlalu besar
- Koneksi tidak stabil
- Project terlalu banyak file
- Agent membaca terlalu banyak context
- Limit hampir habis

Solusi:

1. Pecah task menjadi lebih kecil.
2. Tutup proses Claude Code lalu jalankan ulang.
3. Cek koneksi internet.
4. Cek limit usage.
5. Gunakan prompt yang lebih spesifik.

---

## VS Code Extension

### Setup Claude Code Extension

Langkah umum:

1. Install Claude Code CLI terlebih dahulu.
2. Install extension Claude Code dari VS Code Marketplace jika tersedia.
3. Buka folder project di VS Code.
4. Pastikan API Key sudah diset melalui environment variables atau `settings.json`.
5. Jalankan Claude Code dari sidebar/extension.

---

### Extension tidak mendeteksi Claude Code CLI

Solusi:

1. Pastikan CLI bisa dipanggil dari terminal:

```bash
claude --version
```

2. Restart VS Code.
3. Restart komputer jika perlu.
4. Pastikan PATH npm global sudah benar.
5. Jika extension meminta path CLI manual, arahkan ke lokasi binary `claude`.

---

### Extension tidak bisa akses API Key

Solusi:

1. Gunakan `settings.json` agar lebih stabil.
2. Pastikan file berada di lokasi:

Windows:

```text
C:\Users\NAMA_USER\.claude\settings.json
```

Mac/Linux:

```text
~/.claude/settings.json
```

3. Restart VS Code setelah membuat file.

---

## Limit dan Usage

### Cara cek sisa limit

Buka:

```text
https://ai.bluepack.my.id/usage
```

Limit paket:

```text
220 request / 5 jam
2.200 request / minggu
```

---

### Kenapa 1 prompt bisa mengurangi lebih dari 1 request?

Dalam pemakaian normal, 1 prompt biasanya dihitung sebagai 1 request.

Namun task coding kompleks bisa memakai beberapa request tambahan karena AI dapat:

- Membaca file
- Menganalisis kode
- Melakukan edit
- Retry
- Melanjutkan proses otomatis
- Memanggil tool tambahan

Jadi limit dihitung berdasarkan request API, bukan jumlah chat yang terlihat.

---

### Limit tidak langsung reset

Limit menggunakan sistem rolling window.

Artinya, kuota tersedia kembali secara bertahap mengikuti waktu request sebelumnya, bukan reset serentak pada jam tertentu.

---

## Keamanan

### API Key bocor

Jika API Key bocor:

1. Jangan lanjut menggunakan API Key tersebut.
2. Hubungi seller/admin.
3. Minta pengecekan atau penggantian API Key.
4. Hapus API Key dari screenshot, GitHub, chat publik, atau file yang dibagikan.

---

### Cara aman menyimpan API Key

- Simpan hanya di environment variables atau `settings.json`
- Jangan upload ke GitHub
- Jangan share ke orang lain
- Jangan screenshot terminal yang menampilkan API Key
- Jangan taruh API Key di file project yang bisa ikut ter-commit

---

## Saat Melapor Error ke Admin

Kirim informasi berikut:

- Screenshot error
- Sistem operasi
- Apakah menggunakan VS Code atau CLI/Terminal
- Command terakhir yang dijalankan
- Apakah API Key sudah diset
- Apakah sudah cek limit
- Langkah yang sudah dicoba

```

```
