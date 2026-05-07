# Rate Limit Usage Policy

## Sistem Limit

Layanan ini menggunakan sistem limit berbasis request API.

Limit dihitung berdasarkan request, bukan hanya jumlah chat atau prompt yang diketik.\

## Cek Sisa Limit

Pengguna dapat mengecek usage dan sisa limit melalui:

```text
https://ai.bluepack.my.id/usage
```

## Limit Paket

```text
220 request / 5 jam
2.200 request / minggu
```

## Prompt dan Request

Prompt adalah perintah yang diketik oleh pengguna.

Request adalah hitungan pemakaian API.

Dalam penggunaan normal, 1 prompt biasanya dihitung sebagai 1 request.

Namun untuk task coding yang lebih kompleks, 1 prompt bisa menghasilkan beberapa request tambahan, misalnya ketika AI membaca file, menganalisis kode, melakukan edit, retry, atau menjalankan proses lanjutan.

Jadi limit paket dihitung berdasarkan request API, bukan jumlah prompt atau chat.

## Rolling Window

Limit 5 jam dan weekly limit menggunakan sistem rolling window.

Artinya, kuota tidak selalu reset pada jam tertentu.

Kuota akan tersedia kembali secara bertahap mengikuti waktu request sebelumnya.

Contoh sederhana:

Jika pengguna memakai request pada pukul 10:00, maka request tersebut akan keluar dari hitungan limit 5 jam sekitar pukul 15:00.

## Limit 5 Jam

Limit 5 jam digunakan untuk mencegah pemakaian terlalu besar dalam waktu pendek.

```text
220 request / 5 jam
```

Jika limit ini habis, pengguna perlu menunggu sebagian request lama keluar dari rolling window.

## Weekly Limit

Weekly limit digunakan untuk menjaga pemakaian mingguan tetap wajar.

```text
2.200 request / minggu
```

Jika weekly limit habis, pengguna perlu menunggu kuota mingguan tersedia kembali secara bertahap mengikuti sistem rolling window.

## Jika Mencapai Limit

Jika limit 5 jam atau weekly limit habis, pengguna perlu menunggu hingga kuota tersedia kembali.

Jika mengalami kendala akses, silakan hubungi admin untuk pengecekan.

## Catatan Penggunaan

Gunakan API secara wajar dan efisien.

Hindari:

- Spam request
- Menjalankan banyak agent bersamaan tanpa kebutuhan jelas
- Mengulang prompt yang sama berkali-kali
- Membagikan API Key ke orang lain
- Menggunakan API Key untuk aktivitas yang melanggar aturan platform

Penggunaan berlebihan, spam request, atau penyalahgunaan layanan dapat dibatasi oleh admin.

## Fair Usage

Limit paket sudah diberikan untuk penggunaan normal coding assistant.

Namun admin dapat membatasi, mengganti, atau menonaktifkan akses jika ditemukan:

- API Key dibagikan ke banyak orang
- Pemakaian tidak wajar
- Abuse/spam
- Aktivitas yang berisiko terhadap sistem
- Pelanggaran keamanan

## Catatan Penting

Limit dihitung oleh sistem server.

Jika ada perbedaan antara jumlah prompt yang diketik dan jumlah request yang tercatat, maka data server menjadi acuan utama.

Beberapa aktivitas Claude Code dapat memakai lebih dari 1 request, terutama ketika task melibatkan analisis file, edit kode, retry, tool call, atau proses otomatis lain.
