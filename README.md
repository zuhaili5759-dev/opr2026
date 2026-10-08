# OPR Sekolah — Next.js + Supabase + Vercel

Aplikasi sebenar OPR untuk guru: login, borang, sehingga 6 gambar, simpan Supabase, dashboard, PDF/cetak.

## 1. Supabase
1. Cipta projek Supabase.
2. Authentication → Users → tambah akaun guru/admin (email + password).
3. SQL Editor → jalankan `supabase/schema.sql`.
4. Selepas user dibuat, masukkan profilnya:

```sql
insert into public.profiles(id,full_name,role,school_name)
select id,'Nama Guru','teacher','Nama Sekolah' from auth.users where email='EMAIL_GURU';
```

Untuk pentadbir tukar `role` kepada `admin`.

## 2. Local
```bash
npm install
cp .env.example .env.local
npm run dev
```
Isi URL dan publishable key Supabase dalam `.env.local`.

## 3. Vercel
Import repository GitHub ke Vercel. Set environment variables yang sama:
- NEXT_PUBLIC_SUPABASE_URL
- NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY

Build command: `npm run build`.

## Nota PDF
Versi ini menggunakan halaman cetak HTML yang terus membuka dialog Print. Pilih "Save as PDF" untuk menyimpan PDF. Ini lebih stabil di telefon/desktop dan tidak memerlukan server PDF berat. Struktur PDF boleh ditukar kemudian kepada template rasmi sekolah.
