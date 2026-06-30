# TODO - Integrasi Kasir dengan Backend API

- [x] Konfirmasi scope perubahan dengan user
- [ ] Refactor `kasir.html` sumber data:
  - [ ] Ganti `getOrders/saveOrders` localStorage jadi fetch API `/api/orders`
  - [ ] Ganti data meja jadi fetch API `/api/tables`
  - [ ] Ganti data menu jadi fetch API `/api/menu`
  - [ ] Sesuaikan update status antrian ke API `PATCH /api/orders/:id/status`
  - [ ] Sesuaikan reset/kosongkan meja via API (set status order selesai / hapus bila perlu)
- [ ] Sinkronisasi laporan dari API `/api/reports/sales`
- [ ] Tambahkan auto-refresh kasir agar pembayaran Midtrans dari `3keranjang.html` langsung muncul
- [ ] Testing:
  - [ ] Buat order dari keranjang + bayar Midtrans
  - [ ] Verifikasi order & status tampil di kasir
  - [ ] Verifikasi perubahan status dari kasir tersimpan di backend
