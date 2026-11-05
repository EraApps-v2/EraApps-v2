# EraApps — VS Code

## Menjalankan aplikasi
1. Ekstrak `EraApps-VSCode.zip`.
2. Buka folder `EraApps-VSCode` di Visual Studio Code.
3. Pastikan ekstensi **Live Server** terpasang dan buka `index.html`.
4. Klik **Go Live** pada status bar VS Code untuk menjalankan aplikasi melalui `http://localhost:5500`.
5. Untuk debugging, biarkan Live Server berjalan, buka panel **Run and Debug**, pilih **EraApps: Chrome**, lalu tekan **F5**. Konfigurasi debugger ada di `.vscode/launch.json` dan menggunakan debugger Chrome bawaan VS Code.
6. File proyek tersimpan otomatis oleh VS Code sekitar 1 detik setelah perubahan berhenti.

## Akun demo
- Username: `admin`
- Password: `admin`
- Setelah masuk, pilih **Pencapaian Toko** atau **Pencapaian ERO** pada menu navigasi untuk membuka report.

## Fitur
- Admin dapat membuat akun ERO, Store Leader, dan TSH.
- Admin dapat menghapus akun semua role kecuali akun Admin utama.
- Store Leader dapat membuat dan menghapus akun ERO pada store miliknya.
- Admin dapat menghapus target satu per satu dari daftar target dan pencapaian satu per satu, termasuk data hasil import Excel dan input Erobook. Penghapusan memerlukan konfirmasi dan langsung memperbarui dashboard.
- Admin juga dapat menghapus seluruh data target atau seluruh data pencapaian hasil import Excel sekaligus dari halaman UPDATE. Penghapusan semua pencapaian hasil import tidak menghapus catatan input Erobook.
- Admin dapat import banyak akun melalui file Excel (`.xlsx` / `.xls`).
- Template tersedia di `Template-Import-Akun-EraApps.xlsx` dan bisa diunduh dari halaman Manajemen Akun.
- Menu **Pencapaian Toko** dan **Pencapaian ERO** memisahkan ringkasan target dan pencapaian non-VAS berdasarkan dimensi masing-masing; grafik kategori juga menampilkan Operator dan Repair Contract. AR Tecprotec dihitung sebagai quantity Tecprotec dibagi total quantity Device, Laptop, dan CE, dengan grafik quantity dan pie komposisi mengikuti filter laporan. Ekspor Excel mengikuti menu yang sedang dibuka. Telkomsel, Indosat, XL AXIATA, dan Tecprotec tersedia terpisah pada menu **VAS**.
- Akun ERO memiliki menu **Form Erobook** di samping **Pencapaian ERO** dan tombol dari form untuk membuka laporan pencapaiannya.
- Pada Form Erobook, category Operator hanya menampilkan brand Indosat, Telkomsel, dan XL AXIATA (Carrier tidak ditampilkan). Untuk Accessories, brand tidak perlu dipilih.
- Filter ERO tidak ditampilkan pada akun ERO; laporan otomatis dibatasi ke data ERO yang sedang login.
- Laporan Pencapaian ERO/Toko menampilkan SOB Accessories (nilai Accessories dibagi nilai penjualan di luar Accessories) dan AR Accessories (quantity Accessories dibagi quantity Device). Keduanya mengikuti pilihan periode harian, bulanan, kuartalan, semester, atau tahunan dan tersedia di ekspor Excel.
- Pada category **Repair Contract**, brand yang tersedia adalah **Tecprotec**.
- Filter brand pada laporan dapat dipilih terpisah tanpa memilih category. Grafik menampilkan pencapaian per category, per toko atau ERO, dan tren garis pencapaian serta target per bulan.
- Report VAS menampilkan target, pencapaian, quantity VAS, quantity Device, dan AR (`quantity VAS / quantity Device`) dengan filter periode, toko, dan ERO. Pilihan data mengikuti akses role pengguna.
- Import pencapaian perlu memuat kolom `quantity` agar AR dapat dihitung. Pada Erobook, quantity wajib diisi untuk Device dan VAS. Impor ulang data lama untuk mengisi quantity yang sebelumnya belum tersimpan.

## Format Excel
Gunakan kolom: `Nama`, `Username`, `Password`, `Role`, `Store`. Role yang diterima: `ERO`, `Store Leader`, `TSH`. Password minimal 6 karakter. Username harus unik. Contoh data pada template boleh diganti atau dihapus sebelum diimpor.

## Catatan
Fitur Excel memakai SheetJS dari CDN dan baru memuat library saat fitur Excel digunakan, sehingga halaman utama tidak perlu menunggu unduhan library tersebut. Koneksi internet tetap diperlukan saat memakai import/export Excel. Akun disimpan di `localStorage` browser dan tidak disinkronkan antarperangkat. Ini prototipe front-end, bukan sistem autentikasi aman untuk operasional; untuk penggunaan nyata perlu backend/database dan password hashing.
