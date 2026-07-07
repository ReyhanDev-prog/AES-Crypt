# AES-128 Simulator

Aplikasi simulator AES-128 (Advanced Encryption Standard) untuk enkripsi dan dekripsi data, lengkap dengan visualisasi tahap demi tahap: state matrix per round, proses Key Expansion, dan seluruh operasi internal AES (SubBytes, ShiftRows, MixColumns, AddRoundKey).

## Cara Pemakaian

### 1. Isi Plaintext / Ciphertext

- Pilih tipe input di bagian **Plaintext**: **Teks** (ASCII biasa, maks. 16 karakter) atau **Hex** (32 karakter heksadesimal, merepresentasikan 16 byte).
- Ketik input kamu pada kolom yang tersedia.
  - Mode **Teks**: masukkan kalimat/kata bebas, maksimal 16 karakter (akan otomatis dipadding jika kurang dari 16 byte).
  - Mode **Hex**: masukkan 32 digit hex, misalnya `3243f6a8885a308d313198a2e0370734`.

### 2. Isi Kunci (Key)

- Masukkan **Kunci AES-128** sepanjang 32 karakter hex (setara 128-bit / 16 byte) pada kolom **Kunci**.
- Contoh: `2b7e151628aed2a6abf7158809cf4f3c`
- Kolom akan berubah merah dan menampilkan pesan error jika format key tidak valid (bukan hex atau panjangnya tidak 32 karakter).

### 3. Pilih Mode Operasi

- Klik tombol **🔒 ENKRIPSI** untuk mengenkripsi plaintext menjadi ciphertext.
- Klik tombol **🔓 DEKRIPSI** untuk mendekripsi ciphertext kembali menjadi plaintext.

### 4. Jalankan Proses

- Klik tombol **Run/Proses** (tombol utama berwarna cyan) untuk menjalankan algoritma AES sesuai input dan mode yang dipilih.
- Hasil output (ciphertext/plaintext dalam hex) akan langsung muncul di panel output, beserta input hex yang digunakan.
- Klik ikon **Salin** di pojok kanan atas panel output untuk menyalin hasil ke clipboard.

### 5. Lihat Detail Proses

Setelah proses dijalankan, hasil detail muncul dalam dua tab:

- **🔑 Key Expansion** — menampilkan tabel lengkap ekspansi kunci dari W[0] sampai W[43], termasuk operasi RotWord, SubWord, dan XOR dengan Rcon pada setiap word kelipatan 4.
- **🔒 Proses Enkripsi / 🔓 Proses Dekripsi** — menampilkan visualisasi round-by-round (Round 0 hingga Round 10) dalam bentuk accordion:
  - Klik header setiap round untuk membuka/menutup detailnya.
  - Tombol **Buka Semua** / **Tutup Semua** di atas daftar round untuk expand/collapse semua round sekaligus.
  - Setiap round menampilkan state matrix 4×4 sebelum dan sesudah tiap operasi (SubBytes, ShiftRows, MixColumns, AddRoundKey) beserta round key yang dipakai.

### 6. Coba Contoh Test Vector (Opsional)

Gunakan tombol berikut untuk mengisi otomatis dengan test vector standar NIST FIPS-197 (berguna untuk verifikasi/pembelajaran):

- **📋 NIST App.B** — mengisi PT `3243f6a8885a308d313198a2e0370734` dan Key `2b7e151628aed2a6abf7158809cf4f3c` (hasil CT yang benar: `3925841d02dc09fbdc118597196a0b32`).
- **📋 NIST C.1** — mengisi PT `00112233445566778899aabbccddeeff` dan Key `000102030405060708090a0b0c0d0e0f` (hasil CT yang benar: `69c4e0d86a7b0430d8cdb78070b4c55a`).

### 7. Reset

- Klik tombol **↺ Reset** untuk mengosongkan semua input dan menyembunyikan hasil, agar bisa mulai proses baru dari awal.

## Tips

- Gunakan tombol contoh NIST untuk memverifikasi bahwa hasil enkripsi/dekripsi aplikasi sudah sesuai standar resmi sebelum menggunakan input kustom kamu sendiri.
- Untuk keperluan laporan/tugas, expand semua round (**Buka Semua**) lalu screenshot tiap tahap sebagai bukti proses step-by-step.
- Pastikan panjang key selalu 32 karakter hex (128-bit) — AES-128 tidak menerima panjang key lain.
