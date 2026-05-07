# FAQ - Pertanyaan Umum

## Cek Limit

### Bagaimana cara cek sisa limit?

Gunakan halaman cek limit:

```text
https://ai.bluepack.my.id/usage
```

Masukkan data yang diminta pada halaman tersebut untuk melihat status pemakaian.

---

## Instalasi

### Gimana cara install Claude Code?

Ikuti panduan di `SETUP.md`.

Command utama:

```bash
npm install -g @anthropic-ai/claude-code
```

### Node.js versi berapa yang dibutuhkan?

Minimal Node.js 18.

Cek versi Node.js:

```bash
node --version
```

### Error `npm not found` apa solusinya?

Install Node.js dari website resmi Node.js, lalu restart terminal.

```text
https://nodejs.org
```

### Apakah harus install Git?

Untuk Windows, disarankan install Git for Windows agar Claude Code bisa berjalan lebih lancar.

Download Git:

```text
https://git-scm.com/downloads/win
```

### Berapa lama proses install?

Biasanya kurang dari 5 menit, tergantung kecepatan internet dan kondisi perangkat.

---

## Setup API Key

### API Key format seperti apa?

API Key mengikuti format yang diberikan oleh seller/admin.

Contoh format:

```text
bluepack_...
```

Jangan mengubah, memotong, atau menambahkan karakter pada API Key.

### Berapa kali perlu setup API Key?

Cukup satu kali selama API Key masih aktif.

Jika API Key diganti, lakukan setup ulang dengan API Key baru.

### Mana yang lebih baik, environment variables atau settings.json?

Keduanya bisa digunakan.

Rekomendasi paling mudah:

- Windows: `settings.json`
- Mac/Linux: environment variables atau `settings.json`

### Apakah aman menyimpan API Key di settings.json?

Aman selama file tersebut tidak dibagikan dan tidak di-commit ke GitHub.

Jangan pernah share API Key ke orang lain.

---

## Penggunaan

### Bagaimana cara start Claude Code?

Melalui terminal:

```bash
claude
```

Melalui VS Code:

- Buka VS Code
- Buka project
- Jalankan Claude Code dari extension/sidebar jika tersedia

### Apakah Claude Code bisa membaca file project?

Ya. Claude Code bisa membaca context dari file dalam folder project yang sedang dibuka atau dijalankan.

### Command apa saja yang sering dipakai?

```text
/status  - cek status dan konfigurasi
/cost    - lihat token usage
/model   - cek atau ganti model jika tersedia
/exit    - keluar
```

### Apakah bisa offline?

Tidak. Claude Code membutuhkan koneksi internet.

---

## Prompt dan Request

### Apa itu prompt?

Prompt adalah perintah yang kamu kirim ke Claude Code melalui VS Code atau CLI/Terminal.

### Apa itu request?

Request adalah hitungan penggunaan API.

Dalam pemakaian normal, 1 prompt biasanya dihitung sebagai 1 request.

Namun untuk proses coding yang kompleks, 1 prompt bisa memakai beberapa request tambahan karena AI dapat membaca file, menganalisis kode, melakukan edit, retry, atau melanjutkan proses otomatis.

Jadi limit paket dihitung berdasarkan request API, bukan jumlah chat.

---

## Paket dan Limit

### Apa paket yang tersedia?

Saat ini tersedia 1 paket utama dengan pilihan durasi:

- 1 Hari
- 7 Hari
- 14 Hari
- 21 Hari
- 30 Hari

### Berapa limit paket?

Limit paket:

```text
220 request / 5 jam
2.200 request / minggu
```

### Apakah limit reset setiap jam tertentu?

Tidak.

Limit menggunakan sistem rolling window.

Artinya, kuota akan tersedia kembali secara bertahap mengikuti waktu pemakaian sebelumnya.

### Apa yang terjadi jika limit habis?

Jika limit 5 jam atau weekly limit habis, pengguna perlu menunggu kuota tersedia kembali.

Jika ada kendala akses, hubungi admin untuk pengecekan.

---

## Model

### Apakah bisa memilih model?

Model mengikuti ketersediaan sistem.

Jika command `/model` menampilkan pilihan, pengguna bisa mencoba memilih model dari daftar yang tersedia.

### Apakah support semua model Anthropic?

Layanan ini menggunakan format Claude Code compatible API.

Model yang tersedia mengikuti konfigurasi sistem dari seller/admin.

---

## Keamanan

### Apakah aman share API Key?

Tidak.

Siapa pun yang memiliki API Key dapat menggunakan kuota kamu.

### Apa yang harus dilakukan jika API Key bocor?

Hubungi admin/seller untuk pengecekan dan penggantian API Key jika diperlukan.

### Cara menjaga API Key

- Jangan share API Key ke orang lain
- Jangan upload API Key ke GitHub
- Jangan screenshot terminal yang menampilkan API Key
- Simpan API Key hanya di environment variables atau settings.json

---

## Support

### Bagaimana jika masih bingung?

Baca `SETUP.md` terlebih dahulu.

Jika masih ada kendala, hubungi seller/admin.

### Apa yang harus dikirim saat melapor error?

Kirim informasi berikut:

- Sistem operasi yang digunakan
- Screenshot error
- Langkah yang sudah dicoba
- Apakah menggunakan VS Code atau CLI/Terminal
