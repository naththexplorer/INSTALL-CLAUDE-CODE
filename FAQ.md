# FAQ - Pertanyaan Umum

## Instalasi

**Gimana cara install?**
Ikuti SETUP.md atau jalankan: `npm install -g @anthropic-ai/claude-code`

**Node.js versi berapa yang dibutuhkan?**
Minimal 18. Cek dengan: `node --version`

**Error "npm not found" apa solusinya?**
Install Node.js dari nodejs.org, restart terminal.

**Apakah harus install Git?**
Hanya di Windows. Download dari git-scm.com/downloads/win

**Berapa lama install-nya?**
Kurang dari 5 menit tergantung kecepatan internet.

## Setup API Key

**API Key format seperti apa?**
Dimulai dengan `sk-cp-` diikuti karakter panjang. Contoh: `sk-cp-xxxxxxxxxxxxx`

**Berapa kali saya perlu setup API Key?**
Cukup satu kali. Environment variables atau settings.json bersifat permanent.

**Mana yang lebih baik, environment variables atau settings.json?**
Sama saja. Pilih yang lebih mudah buat Anda.

**Bagaimana jika saya ubah API Key?**
Setup ulang dengan API Key baru. Tutup dan buka terminal baru.

**Apakah aman simpan API Key di settings.json?**
Lebih aman dari hardcode. Tapi jangan commit ke Git.

## Penggunaan

**Bagaimana cara start?**
Terminal: `claude`
VS Code: Klik icon Claude di sidebar

**Apakah Claude bisa baca file saya?**
Ya, Claude Code otomatis baca context dari file di folder project Anda.

**Bagaimana cara lihat token usage?**
Gunakan command `/cost` saat ChatCode running.

**Berapa quota saya yang tersisa?**
`/cost` hanya menampilkan token usage, bukan sisa uang. Estimasi saja dari token yang dipakai.

**Command apa saja yang tersedia?**
`/status` - cek config
`/cost` - lihat usage
`/model` - ganti model
`/exit` - keluar

**Apakah bisa menggunakan model lain?**
Coba `/model` untuk lihat opsi. API ini optimized untuk Claude.

**Bisa offline tidak?**
Tidak, butuh internet connection.

## Biaya & Quota

**Berapa lama API $10 akan bertahan?**
Estimasi 1-4 minggu tergantung seberapa sering dipakai. Light usage (~1-2 chat/hari) bisa bertahan 1-2 bulan.

**Apa yang terjadi jika quota habis?**
API Key tidak bisa dipakai. Beli API Key baru dari seller.

**Apakah ada unlimited plan?**
Tanya seller. Paket ini adalah $10 dengan quota terbatas.

**Bagaimana cara tracking usage?**
Gunakan `/cost` command untuk lihat token breakdown.

## Keamanan

**Apakah aman share API Key?**
Tidak. Siapa pun yang punya API Key bisa pakai quota Anda.

**Jika API Key ter-leak apa yang harus dilakukan?**
Hubungi seller segera untuk revoke API Key lama dan dapat yang baru.

**Bagaimana cara protect API Key?**
- Jangan share dengan orang lain
- Jangan commit ke Git
- Jangan screenshot terminal dengan API Key
- Gunakan environment variables atau settings.json

**Apakah Claude Code mencuri data saya?**
Tidak. Data cuma dikirim ke API Anthropic untuk processing, bukan disimpan.

## Troubleshooting

**"Invalid API Key" apa solusinya?**
- Pastikan API Key benar (cek typo)
- Pastikan environment variables ter-set
- Buka terminal baru setelah setup
- Jika pakai settings.json, cek path-nya benar

**"command not found: claude"**
- Jalankan: `npm install -g @anthropic-ai/claude-code`
- Restart komputer jika perlu
- Cek Node.js terinstall dengan: `node --version`

**VS Code Extension tidak muncul**
- Tutup VS Code sepenuhnya
- Restart komputer
- Buka VS Code lagi
- Pastikan extension terinstall

**"Git Bash required" (Windows)**
- Install Git for Windows dari git-scm.com/downloads/win
- Restart terminal

**Koneksi lambat/timeout**
- Cek internet connection
- Restart terminal atau VS Code
- Coba lagi nanti

**Bagaimana cara uninstall?**
```
npm uninstall -g @anthropic-ai/claude-code
rm -rf ~/.claude    # atau %USERPROFILE%\.claude di Windows
```

## Kompatibilitas

**Sistem operasi apa saja yang didukung?**
Windows 10+, macOS 13+, Ubuntu 20.04+, Debian 10+, dan distro Linux lain.

**Bisakah digunakan di server atau cloud?**
Bisa, asal ada Node.js 18+ dan internet connection.

**Apakah bisa di docker atau container?**
Bisa, setup sama seperti di Linux biasa.

**Bagaimana dengan WSL (Windows Subsystem for Linux)?**
Bisa. Setup sama seperti Linux.

## Fitur & Capabilities

**Apa saja yang bisa dilakukan dengan Claude Code?**
- Code review
- Debugging
- Generate code
- Explain code
- Brainstorming
- Technical writing
- Dan banyak lagi sesuai capability Claude

**Apakah bisa automate task?**
Bisa, tapi Claude Code yang ini lebih untuk interactive chat. Untuk automation yang proper, gunakan Claude API langsung.

**Bagaimana jika saya punya file besar?**
Claude Code bisa baca file besar, tapi ada context limit. Jika file terlalu besar, bagi jadi bagian-bagian.

**Apakah bisa menggunakan plugin?**
Tidak, Claude Code CLI tidak support plugin.

## Support & Contact

**Bagaimana jika masih ada pertanyaan?**
- Baca SETUP.md lagi
- Cari di FAQ ini
- Hubungi seller

**Apakah ada dokumentasi lebih lengkap?**
Baca SETUP.md. Semua instruksi ada disana.

**Bagaimana kalau saya ketemu bug?**
Laporkan ke seller dengan detail tentang apa yang terjadi, OS Anda, dan step untuk reproduce.

---

Jika masih bingung, hubungi seller atau baca SETUP.md.
