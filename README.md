# AES-128 Simulator

Simulator AES-128 (encrypt/decrypt) berbasis single-file HTML/CSS/JS, lengkap dengan visualisasi state matrix per round dan Key Expansion.

## Struktur Project

```
aes-deploy/
├── public/
│   └── index.html      # aplikasi utama (semua HTML/CSS/JS dalam 1 file)
├── vercel.json          # konfigurasi deploy Vercel
├── package.json
└── .gitignore
```

## Cara Deploy ke Vercel

### Opsi 1 — Vercel CLI (paling cepat)

1. Install Vercel CLI (jika belum ada):
   ```bash
   npm install -g vercel
   ```
2. Masuk ke folder project:
   ```bash
   cd aes-deploy
   ```
3. Login (sekali saja):
   ```bash
   vercel login
   ```
4. Deploy:
   ```bash
   vercel
   ```
   Ikuti prompt (pilih scope, nama project, dll — default saja sudah cukup).
5. Untuk deploy ke production:
   ```bash
   vercel --prod
   ```

### Opsi 2 — Lewat GitHub + Dashboard Vercel

1. Push folder ini ke repository GitHub baru:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: AES-128 Simulator"
   git branch -M main
   git remote add origin <URL_REPO_GITHUB_KAMU>
   git push -u origin main
   ```
2. Buka https://vercel.com/new
3. Import repository GitHub tersebut.
4. Vercel akan otomatis mendeteksi ini sebagai static project (karena ada `vercel.json`). Tidak perlu setting Build Command atau Output Directory secara manual — biarkan default.
5. Klik **Deploy**.

### Opsi 3 — Drag & Drop (paling simpel, tanpa CLI/Git)

1. Buka https://vercel.com/new
2. Pilih tab "Deploy" lalu drag folder `aes-deploy` (atau langsung folder `public` berisi `index.html`) ke area upload.
3. Vercel akan langsung deploy sebagai static site.

## Custom Domain (opsional)

Setelah deploy berhasil, kamu bisa tambahkan domain custom (misalnya `.my.id` atau `.vercel.app` custom subdomain) lewat:
Project Settings → Domains → Add Domain.

## Catatan

- Tidak ada backend/API, tidak ada dependency npm yang perlu di-install — murni static HTML.
- Tidak perlu environment variable apapun.
- File utama ada di `public/index.html`, jangan dipindah lokasinya karena `vercel.json` merujuk ke path tersebut.
