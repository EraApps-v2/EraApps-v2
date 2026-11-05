# Report

## Menjalankan aplikasi
1. Ekstrak `EraApps-VSCode.zip`.
2. Buka folder root `eraapps-cloud` di Visual Studio Code agar Report dan EraApps-V2 berjalan pada origin yang sama.
3. Pastikan ekstensi **Live Server** terpasang, lalu jalankan Live Server dari `index.html` di root proyek.
4. Buka `http://localhost:5500/EraApps-VSCode/index.html` untuk Report. Report akan memakai sesi EraApps-V2 yang sudah aktif; jika belum ada sesi, masuk melalui halaman EraApps-V2 terlebih dahulu.
5. Untuk debugging, biarkan Live Server berjalan, buka panel **Run and Debug**, pilih **EraApps: Chrome**, lalu tekan **F5**. Konfigurasi debugger ada di `.vscode/launch.json` dan menggunakan debugger Chrome bawaan VS Code.
6. File proyek tersimpan otomatis oleh VS Code sekitar 1 detik setelah perubahan berhenti.

## Login dan role
- Report membaca sesi, akun, status persetujuan, serta role dari Supabase EraApps-V2.
- Role Admin, LOB, TSH, Store Leader, dan ERO mendapat tampilan sesuai cakupan organisasinya. Promotor belum memiliki akses Report.
- Kelola akun melalui EraApps-V2; halaman Report hanya menampilkan akun yang dapat dilihat oleh role aktif.

## Fitur
- Akun dan role tidak disimpan atau dibuat di browser Report; keduanya mengikuti database EraApps-V2.
- Admin dapat menghapus target satu per satu dari daftar target dan pencapaian satu per satu, termasuk data hasil import Excel dan input Erobook. Penghapusan memerlukan konfirmasi dan langsung memperbarui dashboard.
- Admin juga dapat menghapus seluruh data target atau seluruh data pencapaian hasil import Excel sekaligus dari halaman UPDATE. Penghapusan semua pencapaian hasil import tidak menghapus catatan input Erobook.
- Menu **Pencapaian Toko** dan **Pencapaian ERO** memisahkan ringkasan target dan pencapaian non-VAS berdasarkan dimensi masing-masing; grafik kategori juga menampilkan Operator dan Repair Contract. AR Tecprotec dihitung sebagai quantity Tecprotec dibagi total quantity Device, Laptop, dan CE, dengan grafik quantity dan pie komposisi mengikuti filter laporan. Ekspor Excel mengikuti menu yang sedang dibuka. Telkomsel, Indosat, XL AXIATA, dan Tecprotec tersedia terpisah pada menu **VAS**.
- Akun ERO memiliki menu **Form Erobook** di samping **Pencapaian ERO** dan tombol dari form untuk membuka laporan pencapaiannya.
- Pada Form Erobook, category Operator hanya menampilkan brand Indosat, Telkomsel, dan XL AXIATA (Carrier tidak ditampilkan). Untuk Accessories, brand tidak perlu dipilih.
- Filter ERO tidak ditampilkan pada akun ERO; laporan otomatis dibatasi ke data ERO yang sedang login.
- Laporan Pencapaian ERO/Toko menampilkan SOB Accessories (nilai Accessories dibagi nilai penjualan di luar Accessories) dan AR Accessories (quantity Accessories dibagi quantity Device). Keduanya mengikuti pilihan periode harian, bulanan, kuartalan, semester, atau tahunan dan tersedia di ekspor Excel.
- Pada category **Repair Contract**, brand yang tersedia adalah **Tecprotec**.
- Filter brand pada laporan dapat dipilih terpisah tanpa memilih category. Grafik menampilkan pencapaian per category, per toko atau ERO, dan tren garis pencapaian serta target per bulan.
- Report VAS menampilkan target, pencapaian, quantity VAS, quantity Device, dan AR (`quantity VAS / quantity Device`) dengan filter periode, toko, dan ERO. Pilihan data mengikuti akses role pengguna.
- Import pencapaian perlu memuat kolom `quantity` agar AR dapat dihitung. Pada Erobook, quantity wajib diisi untuk Device dan VAS. Impor ulang data lama untuk mengisi quantity yang sebelumnya belum tersimpan.

## Catatan
Report berbagi sesi login EraApps-V2 melalui Supabase Auth. Dataset target, pencapaian, dan Erobook masih tersimpan di `localStorage` browser; hanya identitas, akun, dan role yang dibaca dari database bersama. Koneksi internet diperlukan untuk autentikasi dan fitur Excel.
