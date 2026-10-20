# CRUDLAB — Landing publik + Admin CRUD (demo lokal)

Aplikasi ini memisahkan halaman publik dan panel admin:
- `index.html`: landing page publik, tidak perlu login dan tidak menampilkan tautan login admin.
- `admin-login.html`: halaman login admin yang hanya dapat dibuka dengan URL langsung.
- `admin.html`: panel CRUD, wajib melewati pemeriksaan sesi admin di JavaScript.
- Konten berstatus **Dipublikasikan** tampil di landing page.
- Konten berstatus **Draft** hanya tampil di panel admin.
- Data disimpan di `localStorage` browser yang sama.

## Menjalankan di VS Code

1. Ekstrak ZIP.
2. Buka folder `crudlab-public-admin` di VS Code.
3. Instal ekstensi Live Server jika belum ada.
4. Klik kanan `index.html` → **Open with Live Server**.
5. Landing page publik akan terbuka. Pengunjung tidak perlu login.
6. Untuk panel admin, masukkan URL langsung: `http://127.0.0.1:5500/admin-login.html` (port dapat berbeda sesuai Live Server).
7. Kredensial demo: username `admin`, password `admin123`.
8. Tambah informasi di panel admin. Centang **Tampilkan di landing page** agar informasi muncul di halaman publik.
9. Klik **Lihat situs** atau kembali ke landing page untuk melihat hasilnya.

## File proyek

```text
crudlab-public-admin/
├── index.html
├── admin-login.html
├── admin.html
└── assets/
    ├── css/styles.css
    └── js/
        ├── common.js
        ├── admin-auth.js
        ├── admin.js
        └── public.js
```

Bootstrap 4.6 dan Google Fonts dimuat dari CDN, jadi koneksi internet dibutuhkan untuk styling/font CDN. Logika aplikasi dan penyimpanan demo berjalan di browser.

## Catatan keamanan — penting

Ini hanya prototipe lokal. Login admin berbasis JavaScript dan `localStorage` bukan pengamanan sungguhan:
- Kredensial admin bisa ditemukan dari source code.
- Sesi dapat dimanipulasi melalui DevTools/localStorage.
- URL yang tidak ditautkan dari landing page bukan URL rahasia; siapa pun yang mengetahuinya dapat membukanya.
- Data localStorage hanya tersedia di browser/perangkat yang sama dan dapat diedit oleh pengguna browser tersebut.
- Jangan gunakan untuk data sensitif atau deployment produksi.

Untuk keamanan nyata, autentikasi dan pemeriksaan hak akses harus dilakukan di server atau layanan seperti Supabase/Firebase, disertai aturan akses database.
