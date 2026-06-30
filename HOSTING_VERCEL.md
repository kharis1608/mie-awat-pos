# Cara Hosting di Vercel (Mode API Routes)

## ⚠️ PENTING: Batasan Penyimpanan

Vercel menggunakan **serverless functions** yang bersifat **ephemeral** (data tidak bertahan antar request). Untuk aplikasi POS dengan data persistent, gunakan **Railway/Render** seperti di `HOSTING.md`.

Alternatif: Gunakan database gratis seperti **Turso (SQLite)** atau **Redis**.

---

## Langkah Hosting di Vercel

### 1. Push ke GitHub
```bash
git init
git add .
git commit -m "init"
# Buat repo baru di github.com, lalu:
git remote add origin https://github.com/username/repo.git
git push -u origin main
```

### 2. Konfigurasi Vercel

Buat file `vercel.json` di root:
```json
{
  "version": 2,
  "builds": [
    { "src": "api/**/*.js", "use": "@vercel/node" }
  ],
  "routes": [
    { "src": "/api/(.*)", "dest": "/api/$1" }
  ]
}
```

### 3. Convert Server ke API Routes

File Express `/backend/server.js` perlu dipecah menjadi endpoint-endpoint terpisah di folder `/api/`:

```
ptti/
├── api/
│   ├── tables.js      # GET /api/tables, PATCH /api/tables/:id
│   ├── menu.js       # GET/POST/DELETE /api/menu
│   ├── orders.js     # GET/POST/DELETE /api/orders
│   ├── payments.js   # GET/POST/DELETE /api/payments
│   ├── reports.js    # GET /api/reports/sales
│   └── settings.js   # GET/PATCH /api/settings
├── vercel.json
└── ... (file HTML lainnya)
```

### 4. Deploy ke Vercel

1. Buka https://vercel.com
2. Login → "New Project" → Import GitHub repo
3. Tambahkan Environment Variables:
   ```
   MIDTRANS_IS_PRODUCTION=false
   MIDTRANS_SERVER_KEY=...
   MIDTRANS_CLIENT_KEY=...
   ```
4. Deploy

---

## Struktur API Routes untuk Vercel

### Contoh: api/tables.js
```javascript
const headers = {
  'Access-Control-Allow-Origin': '*',
  'Access-Control-Allow-Methods': 'GET, POST, PATCH, DELETE, OPTIONS',
  'Access-Control-Allow-Headers': 'Content-Type'
};

export default function handler(req, res) {
  res.setHeader(...headers);
  
  if (req.method === 'OPTIONS') {
    return res.status(200).end();
  }
  
  // Implementasi endpoint tables
  // ...
  
  res.status(200).json({ /* response */ });
}
```

---

## Rekomendasi

Untuk **aplikasi POS yang真正** (data harus bertahan), gunakan:

| Platform | Gratis? | Notes |
|----------|---------|-------|
| Railway | ✅ ($5/bln) | Easy setup, persistence |
| Render | ✅ | Gratis tier tersedia |
| Fly.io | ✅ | Persistence + Docker |
| Railway + Turso (SQLite) | ✅ | solusi gratis terbaik |

**Jangan gunakan Vercel untuk POS** kecuali Anda добавий external database.
