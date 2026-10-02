# absensi-pro-config

Pengaturan Absensi Pro yang bisa diubah **tanpa merilis ulang aplikasi**.

File: `ios/config.json`

## Cara mengubah ambang kemiripan wajah

1. Buka `ios/config.json`
2. Ubah angka `faceMatchThreshold`
3. Commit. Aplikasi akan memakainya saat dibuka berikutnya.

### Arah angka — BACA SEBELUM MENGUBAH

| Perubahan | Artinya | Risikonya |
|---|---|---|
| **Turunkan** (10 -> 8) | Lebih **ketat** | Karyawan asli bisa ditolak |
| **Naikkan** (10 -> 12) | Lebih **longgar** | **Orang lain bisa lolos absen** |

Menaikkan jauh lebih berbahaya. Kalau ragu, pilih yang lebih ketat.

Ubah sedikit demi sedikit (maksimal 1.0 sekali jalan), lalu amati.

### Pagar pengaman di aplikasi

- Rentang sah **4.0 - 20.0**. Di luar itu nilainya **ditolak**, aplikasi memakai bawaan 10.0.
  Ini mencegah satu salah ketik mengunci semua karyawan.
- Kalau file ini tidak bisa diambil (GitHub mati, karyawan offline, JSON rusak),
  aplikasi memakai nilai tersimpan terakhir atau bawaan. **Absen tidak pernah diblokir
  karena file ini.**
- Nilai diambil saat aplikasi dibuka, lalu disimpan di HP.

## Catatan

- Repo ini **publik** supaya aplikasi bisa membacanya tanpa kunci. Token akses tidak bisa
  disembunyikan di dalam aplikasi yang terpasang di HP orang lain — siapa pun bisa
  membongkarnya.
- **JANGAN** menaruh data karyawan, kredensial, atau apa pun yang rahasia di sini.
- `schemaVersion` jangan diubah tanpa koordinasi: aplikasi versi lama memakainya untuk
  memastikan ia mengerti bentuk file ini.
