# Mie Ayam Bangka Awat - Point of Sale System

Sistem kasir dan manajemen restoran untuk Mie Ayam Bangka Awat.

## Fitur
- Menu & Keranjang (Pemesanan)
- Integrasi Midtrans (Pembayaran)
- Kasir Dashboard
- Manajemen Meja
- Laporan Penjualan

## Cara Jalankan (Local)

### Backend (Node.js)
```bash
cd backend
npm install
node server.js
```

Buka http://localhost:3000

---

## Cara Deploy ke Vercel

### 1. Push ke GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/username/repo.git
git push -u origin main
```

### 2. Di Vercel Dashboard
1. Login ke https://vercel.com
2. Klik **New Project** → Import repo GitHub
3. Framework Preset: **Other**
4. Build Command: `npm install`
5. Output Directory: `.`
6. Deploy!

### 3. Setup Environment Variables
Setelah deploy, ke **Settings** → **Environment Variables**:
```
MIDTRANS_IS_PRODUCTION=false
MIDTRANS_SERVER_KEY=( dari Midtrans Dashboard )
MIDTRANS_CLIENT_KEY=( dari Midtrans Dashboard )
```
Lalu **Redeploy**.

### Halaman
- http://localhost:3000/1index.html - Beranda
- http://localhost:3000/2menu.html - Menu
- http://localhost:3000/3keranjang.html - Keranjang
- http://localhost:3000/kasir.html - Kasir
