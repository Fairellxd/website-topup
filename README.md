# TopUpKu — starter website top up game

## 1. Jalankan
```bash
npm install
npm run dev
```
Buka http://localhost:3000

## 2. Database
Buat project Supabase lalu jalankan `supabase/schema.sql`.
Isi `.env.local` dari `.env.example`.

## 3. Pembayaran
Contoh backend sudah menyediakan endpoint webhook Midtrans dengan verifikasi signature.
Sebelum production:
- buat akun merchant/payment gateway sesuai syarat penyedia;
- gunakan Sandbox untuk testing;
- isi server key hanya di environment server;
- set webhook HTTPS;
- verifikasi status pembayaran di server;
- proses webhook secara idempotent.

## 4. Provider top-up
`TOPUP_PROVIDER_API_KEY` dan `TOPUP_PROVIDER_BASE_URL` hanya placeholder.
Integrasikan provider resmi yang menyediakan API untuk produk game yang memang kamu jual.
Jangan menganggap pembayaran sukses hanya berdasarkan redirect/browser.

## 5. Production checklist
- RLS + server-side authorization
- rate limit checkout/webhook
- validasi nominal dari database, bukan harga dari browser
- idempotency order/payment/top-up
- audit log admin
- secret keys tidak boleh `NEXT_PUBLIC_*`
- halaman terms, privacy, refund/contact
- uji sandbox sebelum live

> Untuk pengguna di bawah 18 tahun, pendaftaran merchant/rekening/payment gateway harus mengikuti syarat umur dan melibatkan orang tua/wali bila diperlukan. Jangan memalsukan identitas.
