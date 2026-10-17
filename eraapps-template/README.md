# EraApps Template

Template aplikasi absensi barcode berbasis web. Folder ini dipisahkan dari situs produksi dan tidak menyertakan kredensial, akun, atau data produksi.

## Demo publik lokal

Buka `demo.html` di browser. Demo dapat dinavigasi tanpa login dan memakai data fiktif yang hanya tertulis di halaman. Demo tidak menyimpan atau mengirim data.

## Isi paket

- `index.html`: aplikasi utama.
- `i18n.js`: pilihan bahasa.
- `supabase-cloud.js`: integrasi frontend Supabase.
- `supabase-config.js`: konfigurasi placeholder; ganti dengan proyek milik pembeli.
- `demo.html`: pratinjau publik tanpa login.

Menu promo mendukung pencarian, folder yang dibuka saat diklik, dan ukuran gambar otomatis mengikuti orientasi portrait atau landscape. Upload folder menyimpan file-file di dalamnya. Hanya admin yang dapat menghapus folder atau promo; role lain dapat mengunduh.

Tanggal akhir promo disimpan pada metadata `app_settings`. Aplikasi menghapus folder beserta file Storage saat tanggal lewat jika sesi admin masih terbuka, atau ketika admin masuk kembali. Penghapusan tepat waktu saat tidak ada sesi admin memerlukan scheduler server Supabase; scheduler dan migrasi backend tidak termasuk di paket ini.

## Menyiapkan aplikasi utama

1. Buat proyek Supabase baru khusus untuk pembeli atau lingkungan mereka. Jangan gunakan proyek produksi EraApps.
2. Isi `url` dan `anonKey` pada `supabase-config.js` dengan URL proyek dan publishable/anon key milik mereka.
3. Siapkan schema database, kebijakan Row Level Security, Edge Functions, dan bucket Storage yang dipakai oleh `supabase-cloud.js`. Backend tersebut tidak disertakan dalam paket ini.
4. Uji seluruh alur login, role, upload, dan akses data dengan akun uji sebelum deploy.
5. Deploy folder ini ke hosting statis mereka. Untuk Netlify CLI, tautkan folder ke situs baru milik pembeli lalu jalankan `netlify deploy --prod --dir .`.

Key publishable/anon memang dipakai pada frontend, tetapi akses data tetap harus dibatasi dengan RLS dan validasi backend. Jangan menaruh service-role key atau password di file frontend.

## Batasan dan hak distribusi

Paket ini adalah salinan source frontend dari workspace. Schema/backend Supabase, akun, data, aset berlisensi pihak ketiga, serta dukungan instalasi tidak termasuk. Pastikan Anda memiliki hak untuk mendistribusikan dan menjual source ini, serta tetapkan lisensi dan dukungan untuk pembeli sebelum penjualan.
