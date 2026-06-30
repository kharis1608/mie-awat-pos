# Cara Deploy ke Vercel dengan preset "Node"

## Langkah-langkah Vercel

### 1. Di Vercel Dashboard
1. Login ke https://vercel.com
2. Klik **"New Project"**
3. Import repo GitHub Anda
4. Pada bagian **"Configure Project"**:

| Setting |-value |
|--------|-------|
| Framework Preset | **Other** atau **Node** (pilih yang ada) |
| Build Command | `npm install` |
| Output Directory | `.` |
| Install Command | `npm install` |

5. Klik **Deploy**

---

### 2. Setup Environment Variables
Setelah Deploy selesai:
1. Buka **Settings** → **Environment Variables**
2. Tambahkan variabel:
```
MIDTRANS_IS_PRODUCTION=false
MIDTRANS_SERVER_KEY=(dari Midtrans Dashboard)
MIDTRANS_CLIENT_KEY=(dari Midtrans Dashboard)
```

3. Redeploy (klik **"Deploy"** again)

---

## Catatan Penting untuk Vercel

### ⚠️ Limitasi Vercel untuk POS
- Vercel menggunakan **serverless functions** (data tidak persist)
- Setiap kali function di-refresh, data hilang
- Cocok untuk website static, tapi tidak untuk aplikasi POS dengan data

### ✅ Rekomendasi Lebih Baik
Gunakan **Railway** atau **Render** seperti di `HOSTING.md` untuk aplikasi POS.

---

## Alternative Lain (bukan Vercel)

### Render.com (Gratis)
1. Buka https://render.com
2. New Web Service → Connect GitHub
3. Build Command: `npm install`
4. Start Command: `node backend/server.js`
5. Add Environment Variables
6. Deploy

### Railway.app ($5/bln)
1. Buka https://railway.app
2. New Project → Deploy from GitHub
3. Tambahkan Environment Variables
4. Deploy
