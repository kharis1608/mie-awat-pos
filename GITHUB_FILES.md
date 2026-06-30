# File yang Harus Diupload ke GitHub

## Struktur Folder Lengkap

```
ptti/                    ← Root Project
├── 1index.html          ✓ Wajib (Halaman Beranda)
├── 2menu.html            ✓ Wajib (Halaman Menu)
├── 3keranjang.html       ✓ Wajib (Halaman Keranjang)
├── kasir.html            ✓ Wajib (Halaman Kasir Dashboard)
├── api.js                ✓ Wajib (API Helper untuk frontend)
├── README.md             ✓ Wajib (Dokumentasi)
├── HOSTING.md            ✓ Wajib (Panduan Hosting Railway)
├── runtime.txt           ✓ Wajib (Versi Node.js)
│
├── backend/
│   ├── server.js        ✓ Wajib (Backend API Express)
│   ├── db.json          ✓ Wajib (Database JSON)
│   ├── package.json     ✓ Wajib (Dependencies Node.js)
│   ├── package-lock.json ✓ Wajib (Lock file npm)
│   └── .env              ✗ JANGAN (Rahasia - Midtrans Keys)
│
└── backend/public/
    ├── index.html       ✓ Opsional (Backup halaman)
    ├── 2menu.html       ✓ Opsional
    ├── 3keranjang.html  ✓ Opsional
    ├── kasir.html       ✓ Opsional
    ├── admin-db.html   ✓ Opsional (Admin database)
    └── db-view.js       ✓ Opsional
```

---

## Penjelasan Detail

### ✅ WAJIB Diupload (20 file)

| File | Keterangan |
|------|------------|
| `1index.html` | Halaman beranda/restoran |
| `2menu.html` | Halaman tampilan menu |
| `3keranjang.html` | Halaman keranjang pesanan |
| `kasir.html` | Dashboard kasir |
| `api.js` | Helper API untuk fetch data |
| `README.md` | Dokumentasi project |
| `HOSTING.md` | Panduan hosting |
| `runtime.txt` | File iniw 指定 Node.js version (18.x) |
| `backend/server.js` | Server Express utama |
| `backend/db.json` | Database (JSON file) |
| `backend/package.json` | npm dependencies |
| `backend/package-lock.json` | npm lock file |
| `backend/public/*.html` | File backup di public folder |
| `backend/public/db-view.js` | Script untuk view database |

### ✗ JANGAN Diupload

| File | Alasan |
|------|-------|
| `backend/.env` | Contains Midtrans API keys (RAHASIA) |
| `backend/node_modules/` | Tidak perlu, nanti di-install saat deploy |
| `.git/` | Folder git internal |
| `__pycache__/` | Python cache |
| `*.pyc` | Python compiled files |
| `.venv/` | Virtual environment Python |

---

## Cara Mengabaikan File (.gitignore)

Buat file `.gitignore` di root:

```
# Node.js
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Environment
.env
.env.local
.env.*.local

# Python
__pycache__/
*.py[cod]
*$py.class
.venv/
venv/

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Build
dist/
build/
```

---

## Daftar Perintah Git

```bash
# 1. Inisialisasi git (hanya sekali)
git init

# 2. Tambah semua file (kecuali .gitignore)
git add .

# 3. Buat commit
git commit -m "Initial commit - Mie Ayam POS System"

# 4. Hubungkan ke GitHub (ganti dengan URL repo Anda)
git remote add origin https://github.com/USERNAME/REPO.git

# 5. Push ke GitHub
git push -u origin main
```

---

## Catatan Penting

1. **MIDTRANS KEYS**: Pastikan `backend/.env` TIDAK diupload. Jika sudah upload, segera regenerate keys di Midtrans Dashboard.

2. **Database**: File `db.json` akan direset saat deploy pertama kali. Setup ulang setelah deploy.

3. **HTTPS**: Semua deploy ke Railway/Render sudah menggunakan HTTPS otomatis.

4. **Custom Domain**: Bisa ditambahkan setelah deploy di dashboard Railway/Render.
